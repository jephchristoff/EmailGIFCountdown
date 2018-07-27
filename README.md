EmailCountdown
==============

**What does this do?**

Creates a countdown image counting down to a specific time/date for use in email campaigns.

**How does it work?**

This generates an image based on the following variables:

```php
  $image = imagecreatefrompng('images/countdown.png');
  $font = array(
    'size'=>23, // Font size, in pts usually.
    'angle'=>0, // Angle of the text
    'x-offset'=>7, // The larger the number the further the distance from the left hand side, 0 to align to the left.
    'y-offset'=>30, // The vertical alignment, trial and error between 20 and 60.
    'file'=>'./GillSans.ttc', // Font path
    'color'=>imagecolorallocate($image, 55, 160, 130), // RGB Colour of the text
  );
```
**Offsetting Hours, Minutes and Seconds for Design Flexibility**

With the following code, you can treat each number set differently - offsetting to fit any design.

```php
  $textHours = $interval->format('%H'); // Setting format for Hours
	$textMinutes = $interval->format('%I'); // Setting format for Minutes
	$textSeconds = $interval->format('%S'); // Setting format for Seconds
	imagettftext (
	  $image , $font['size'] , $font['angle'] , $font['x-offset'] , $font['y-offset'] , $font['color'] , $font['file'], $textHours
  );
  imagettftext (
    $image , $font['size'] , $font['angle'] , $font['x-offset']+110 , $font['y-offset'] , $font['color'] , $font['file'], $textMinutes
  );
	imagettftext (
	  $image , $font['size'] , $font['angle'] , $font['x-offset']+215 , $font['y-offset'] , $font['color'] , $font['file'], $textSeconds
	);
```
