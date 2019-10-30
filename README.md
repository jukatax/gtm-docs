# gtm-docs
A document with useful information on Google Tag Manager 2019

## DataLayer cap
- The cap of items in the dataLayer is set to 300

## Useful functions
### Custom events
- Only a push with a key "event" can be used as a Custom Event TRIGGER
- Without additional data: `dataLayer.push({event : "customEventNameHere"})`
- With additional data : `dataLayer.push({event : "customEventNameHere", "somekey" : "somevalue"})`
- Version 1 vs 2: Version 1 goes 1 level deep whereas version 2 can drill down the object if it is nested
- The data that is available to the tag that was triggered by the custom trigger should have been pushed before or within the custom tag, any data pushed after will not be available to that TRIGGER

### Methods available to manipulate dataLayer
#### Push
- `dataLayer.push({pageName : "PDP-bananas"})`
     - doesn't overwrite, if the value is diffeent the value gets overwritten, non primitive values get merged if different
     - Arrays are recursively merged overwriting the indeces that already existed : `dataLayer.push({arr : [1,2,3,4,5]})` , `dataLayer.push({arr : [0,6,7]})` will result in `google_tag_manager["GTM-ABC123"].dataLayer.get('arr') = [0,6,7,4,5]`
     - `dataLayer.push({arr : [1,2,3,4,5]})` is equivalent to `dataLayer.push(['arr.push' ,1,2,3,4,5])`
#### Get
- `google_tag_manager["GTM-ABC123"].dataLayer.get('pageName')` returns the value for the key `pageName`

#### Set
- `google_tag_manager["GTM-ABC123"].dataLayer.set('pageName','PDP-bananas')` sets the value for the key `pageName`

#### Reset
- `google_tag_manager["GTM-ABC123"].dataLayer.reset()` purges all stored keys in the dataLayer

## Restrict tag deployment

Follow [this giude](https://developers.google.com/tag-manager/web/restrict)


## Preview mode
### Safari

Follow [this giude](https://www.simoahava.com/gtm-tips/enable-preview-mode-safari-browser/) to enable preview mode in Safari