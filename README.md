# ip2asn

IP address intelligence. Maps IP address to ASN. ASN to prefix.

## Cache Purging

Essential component of this library is the shell script `asn-cache-purge.sh`, which is to be installed into location of your choice and shall be executed hourly using crontab. (Edit parameters as needed.)

## Dependencies

You will need the `whois` package, which you can install with this or similar command:

```
$ apt install whois
```

## Usage

```php
use peterkahl\ip2asn\ip2asn;

$asnObj = new ip2asn;
$asnObj->cacheDir = '/srv/cache';
$temp = $asnObj->getAsn('8.8.8.8'); # Accepts both IPv4 and IPv6

var_dump($temp);

/*
array(7) {
  ["as_number"]=>
  string(5) "15169"
  ["as_prefix"]=>
  string(10) "8.8.8.0/24"
  ["as_prefix_bin"]=>
  string(24) "000010000000100000001000"
  ["as_country_code"]=>
  string(2) "US"
  ["as_isp"]=>
  string(24) "GOOGLE - Google Inc., US"
  ["as_nic"]=>
  string(4) "ARIN"
  ["as_alloc"]=>
  string(0) "NA"
}
*/
```

```php
use peterkahl\ip2asn\ip2asn;

$asnObj = new ip2asn;
$asnObj->cacheDir = '/srv/cache';

# This will get us an array of all prefixes for AS 94, 95, 96.
$temp = $asnObj->ArrayAsn2prefix(array(94, 95, 96);

var_dump($temp);
```
