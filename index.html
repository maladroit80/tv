<?php
header("Access-Control-Allow-Origin: *");

if (!isset($_GET['url'])) {
    http_response_code(400);
    die("No URL");
}

$url = $_GET['url'];

// sécurité minimale
if (!filter_var($url, FILTER_VALIDATE_URL)) {
    http_response_code(400);
    die("Invalid URL");
}

// cURL
$ch = curl_init($url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
curl_setopt($ch, CURLOPT_TIMEOUT, 20);
curl_setopt($ch, CURLOPT_USERAGENT, "Mozilla/5.0");

$data = curl_exec($ch);

if ($data === false) {
    http_response_code(500);
    die("cURL error");
}

$contentType = curl_getinfo($ch, CURLINFO_CONTENT_TYPE);
curl_close($ch);

// 🎯 Si c’est un M3U8 → on réécrit les liens
if (strpos($url, '.m3u8') !== false) {

    header("Content-Type: application/vnd.apple.mpegurl");

    $base = dirname($url);

    $data = preg_replace_callback('/^(?!#)(.*)$/m', function($matches) use ($base) {
        $line = trim($matches[1]);

        if ($line === "") return "";

        // URL complète
        if (filter_var($line, FILTER_VALIDATE_URL)) {
            return "proxy.php?url=" . urlencode($line);
        }

        // URL relative
        return "proxy.php?url=" . urlencode($base . "/" . $line);
    }, $data);

}
// 🎥 segments vidéo
elseif (strpos($url, '.ts') !== false) {
    header("Content-Type: video/mp2t");
}
// autre contenu
else {
    header("Content-Type: " . $contentType);
}

echo $data;
?>
