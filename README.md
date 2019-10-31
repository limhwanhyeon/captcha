<pre><code>
@php
@session_save_path($_SERVER['DOCUMENT_ROOT'] . "/data/session");
@session_start();

$letters = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ';
$len = strlen($letters);
$letter = $letters[rand(0, $len - 1)];
$text_color = imagecolorallocate($image, 0, 0, 0);


$image = imagecreatetruecolor('160', '40');
$background_color = imagecolorallocate($image, 255, 255, 255);
imagefilledrectangle($image, 0, 0, 200, 50, $background_color);

/*$line_color = imagecolorallocate($image, 64, 64, 64);
for ($i = 0; $i < 10; $i++) {
	imageline($image, 0, rand() % 50, 200, rand() % 50, $line_color);
}*/

/*$pixel_color = imagecolorallocate($image, 0, 0, 255);
for ($i = 0; $i < 1000; $i++) {
	imagesetpixel($image, rand() % 200, rand() % 50, $pixel_color);
}*/

for ($i = 0; $i < 6; $i++) {
	$letter = $letters[rand(0, $len - 1)];
	imagestring($image, 5, 15 + ($i * 25), 13, $letter, $text_color);
	$word .= $letter;
}

unset($_SESSION['captcha']);
$_SESSION['captcha'] = $word;

header("Cache-Control: no-cache, must-revalidate");
header('Content-type: image/png');

imagepng($image);
imagedestroy($image);

//$img = imagecreatetruecolor(160, 40); //크기
//$background_color = imagecolorallocate($img, 0, 0, 0);
//imagettftext($img, 50, 0, 50, 10, ImageColorAllocate($img,255,255,255), 'arial.ttf', $captcha);
////imagefilledrectangle($img, 0, 0, 200, 50, $background_color); // 배경색
////imagestring($img, 7, 50, 10, $captcha, 0x000000); //문자 여백, 문자색상
//imagegif($img);
//imagedestroy($img);
@php
</code></pre>
