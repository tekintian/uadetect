

# PHP浏览器检测 手机 PC,平板等 UaDetect

PHP  UserAgent detect, 用于检测访问者的 User Agent是属于手机 平板,还是PC, 用户浏览器名称,操作系统版本,是否微信, 谷歌,火狐等浏览器判断.

> 本项目源于  https://github.com/serbanghita/Mobile-Detect



## PHP集成方法:

1. composer require "tekintian/uadetect"

~~~php
# 载入方式
# 采用autoload.php自动载入方式加载
require_once  __DIR__ . 'vendor/autoload.php';

//使用
$detect = new UaDetect();

// Basic detection.
$detect->isMobile();
$detect->isTablet();

// Magic methods.
$detect->isIphone();
$detect->isSamsung();
// [...]

// Alternative to magic methods.
$detect->is('iphone');

// Find the version of component.
$detect->version('Android');

// Additional match method.
$detect->match('regex.*here');

// Browser grade method.
$detect->mobileGrade();

// Batch methods.
$detect->setUserAgent($userAgent);
$detect->setHttpHeaders($httpHeaders);
<?php
// Check for mobile environment.
if ($detect->isMobile()) {
    // Your code here.
}
<?php
// Check for tablet device.
if($detect->isTablet()){
    // Your code here.
}
<?php
// Check for any mobile device, excluding tablets.
if ($detect->isMobile() && !$detect->isTablet()) {
    // Your code here.
}
<?php
//  Keep the value in $_SESSION for later use
//    and for optimizing the speed of the code.
if(!$_SESSION['isMobile']){
    $_SESSION['isMobile'] = $detect->isMobile();
}
<?php
// Redirect the user to your mobile version of the site.
if($detect->isMobile()){
    header('http://m.yoursite.com', true, 301);
}
<?php
// Include and instantiate the class.
require_once 'Mobile_Detect.php';
$detect = new Mobile_Detect;

// Any mobile device (phones or tablets).
if ( $detect->isMobile() ) {

}

// Any tablet device.
if( $detect->isTablet() ){

}

// Exclude tablets.
if( $detect->isMobile() && !$detect->isTablet() ){

}

// Check for a specific platform with the help of the magic methods:
if( $detect->isiOS() ){

}

if( $detect->isAndroidOS() ){

}

// Alternative method is() for checking specific properties.
// WARNING: this method is in BETA, some keyword properties will change in the future.
$detect->is('Chrome')
$detect->is('iOS')
$detect->is('UCBrowser')
$detect->is('Opera')
// [...]

// Batch mode using setUserAgent():
$userAgents = array(
'Mozilla/5.0 (Linux; Android 4.0.4; Desire HD Build/IMM76D) AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.166 Mobile Safari/535.19',
'BlackBerry7100i/4.1.0 Profile/MIDP-2.0 Configuration/CLDC-1.1 VendorID/103',
// [...]
);
foreach($userAgents as $userAgent){

  $detect->setUserAgent($userAgent);
  $isMobile = $detect->isMobile();
  $isTablet = $detect->isTablet();
  // Use the force however you want.

}

// Get the version() of components.
// WARNING: this method is in BETA, some keyword properties will change in the future.
$detect->version('iPad'); // 4.3 (float)
$detect->version('iPhone') // 3.1 (float)
$detect->version('Android'); // 2.1 (float)
$detect->version('Opera Mini'); // 5.0 (float)
// [...]

~~~



~~~shell
#PS: 如果在composer的过程中遇到 404错误, 则可能是版本已经更新, 请清除本地缓存后重新加载.

composer clear-cache
composer require "tekintian/uadetect"
~~~







