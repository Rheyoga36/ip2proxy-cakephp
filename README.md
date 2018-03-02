# IP2Proxy CakePHP Plugin
[![Latest Stable Version](https://img.shields.io/packagist/v/ip2location/ip2proxy-cakephp.svg)](https://packagist.org/packages/ip2location/ip2proxy-cakephp)
[![Total Downloads](https://img.shields.io/packagist/dt/ip2location/ip2proxy-cakephp.svg?style=flat-square)](https://packagist.org/packages/ip2location/ip2proxy-cakephp)

IP2Proxy CakePHP plugin enables the user to query an IP address if it was being used as open proxy, web proxy, VPN anonymizer and TOR exits. It lookup the proxy IP address from IP2Proxy BIN Data file. Developers can use the API to query all IP2Proxy BIN databases for applications written using CakePHP.


## INSTALLATION
For CakePHP 3.x

1. Run the command: `composer require ip2location/ip2proxy-cakephp` to download the plugin into the CakePHP 3 platform.
2. Download latest IP2Proxy BIN database
    - IP2Proxy free LITE database at https://lite.ip2location.com
    - IP2Proxy commercial database at https://www.ip2location.com/proxy-database
3. Unzip and copy the BIN file into *cakephp/vendor/ip2location/ip2proxy-cakephp/src/Data* folder. 
4. Rename the BIN file to IP2PROXY.BIN.

**Note:** The plugin has included an old BIN database for your testing and development purpose. 
You may want to download a latest copy of BIN database as the URL stated above.
The BIN database refers to the binary file ended with .BIN extension, but not the CSV format.
Please select the right package for download.


## USAGE
In this tutorial, we will show you on how to create a **TestsController** to display the IP information.

1. Create a **TestsController** in CakePHP 3 using the below command line
```
php bin/cake bake controller Tests
```
2. Create an empty **index.ctp** file in *cakephp/src/Template/Tests* folder.
3. Open the **cakephp/src/Controller/TestsController.php** in any text editor.
4. Remove the contents in TestsController.php and add the below lines into the controller file.
```
<?php
namespace App\Controller;

use App\Controller\AppController;
use IP2ProxyCakePHP\Controller\IP2ProxyCoresController;

/**
 * Tests Controller
 */
class TestsController extends AppController
{

    /**
     * Index method
     *
     * @return \Cake\Http\Response|void
     */
    public function index()
    {
        $IP2Proxy = new IP2ProxyCoresController();
        $record = $IP2Proxy->get('1.0.241.135');

        echo '<p><strong>IP Address: </strong>' . $record['ipAddress'] . '</p>';
        echo '<p><strong>IP Number: </strong>' . $record['ipNumber'] . '</p>';
        echo '<p><strong>IP Version: </strong>' . $record['ipVersion'] . '</p>';
        echo '<p><strong>Country Code: </strong>' . $record['countryCode'] . '</p>';
        echo '<p><strong>Country: </strong>' . $record['countryName'] . '</p>';
        echo '<p><strong>State: </strong>' . $record['regionName'] . '</p>';
        echo '<p><strong>City: </strong>' . $record['cityName'] . '</p>';
        echo '<p><strong>Proxy Type: </strong>' . $record['proxyType'] . '</p>';
        echo '<p><strong>Is Proxy: </strong>' . $record['isProxy'] . '</p>';
        echo '<p><strong>ISP: </strong>' . $record['isp'] . '</p>';
    }

}
```
5. Enter the URL <your domain>/Tests and run. You should see the information of **1.0.241.135** IP address.



## DEPENDENCIES (IP2PROXY BIN DATA FILE)
This library requires IP2Proxy BIN data file to function. You may download the BIN data file at
* IP2Proxy LITE BIN Data (Free): https://lite.ip2location.com
* IP2Proxy Commercial BIN Data (Comprehensive): https://www.ip2location.com/proxy-database

## SUPPORT
Email: support@ip2location.com

Website: https://www.ip2location.com
