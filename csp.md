# How to work around CSP on local machine for testing purposes

## Google Chrome browser

* Download the `ModHeader` extension from [Google Web Store](https://chrome.google.com/webstore/detail/modheader/idgpnmonknjnojddfkpgkljpfnnfcklj)
* Click on the menu icon in the top left corner and add a new profile
* Name it `CSP <yourwebsite here>`
* Click the `+` button
* Click on `Responce header`
* Set the new header name to : `Content-Security-Policy`
* Set the value to : `script-src 'self' 'unsafe-inline' 'unsafe-eval' *`
* Navigate to the website you would like to mofidify the CSP
* Click the "+" button
* Click on `Filter`
* Scroll down  and make sure your website is listed under `Filters` with wildcard at the end `*` which means the enitre website
* You can now inject any script from any source on this website locally on your machine

![modheader image](https://raw.githubusercontent.com/jukatax/gtm-docs/master/assets/modheader_00.jpg "modheader")