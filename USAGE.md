<!-- Start SDK Example Usage [usage] -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->bridgeWallets->list(

);

if ($response->bridgeWalletsList !== null) {
    // handle response
}
```
<!-- End SDK Example Usage [usage] -->