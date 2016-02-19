# Property `facebook`

The property `facebook` allows you to set the required facebook app's properties `appid` and `redirect_uri`. 
The property value should be a nested JSON object. 
The following table lists all its sub-properties:

## Facebook sub-properties

| Property | Value | Description                                     |
|:---------|-------|-------------------------------------------------|
| [appid](https://developers.facebook.com/apps/) | _string_ | The required ID of a Facebook app. By default, this field automatically gets the value of the Copernica appid.  |
| redirect_uri | _string_ | The required URL to redirect to after a person clicks a button on the dialog. By default, this field automatically gets the value of the Copernica website.   |
 
## Example

The following input JSON shows a facebook basic usage in a share block:

```javascript
{
    "from" : "info@example.com",
    "subject" : "Email with a share block",
    "content" : {
        "blocks" : [ {
            "type"      : "share",
            "label"     : "Tell your friends about us!",
            "align"     : "left",
            "icon"      : {
                "type"      : "rounded",
                "size"      : 32
            },
            "link"      : {
                "url"       : "https://responsiveemail.com/",
                "title"     : "Post title"
            },
            "description"   : "Optional prefilled text to share",
            "platforms" : ["facebook"],
            "facebook"  : {
                "appid"        :   "0123456789",
                "redirect_uri" :   "https://www.copernica.com"
            }
        } ]
    }
}
```

For more information and more examples, please check the documentation of the `share` block.