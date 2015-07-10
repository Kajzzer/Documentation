# Property `content`

The actual layout and style of the responsive email is specified in the top-level 
property `content`. This is a nested property in the input JSON that holds a whole 
list of other properties to specify the content of the responsive email, and what 
the email looks like. Alternatively you can provide a normal string to the 
`content` property, which will be the direct html for eventual mime output. This 
however most likely won't be responsive as this is entirely up to you, you can 
consider this to be an advanced feature.

## 580 pixels wide centered content

All emails generated by the responsiveemail.com API have a fixed central column 
of 580px wide that holds all the texts and images. This restriction was necessary 
to ensure that generated mails are compatible with the vast majority of email 
clients. It is exactly this central content that is covered by the top level 
`content` property. The styling properties that you set *inside* the `content` 
property, apply to this central content, and the blocks that you include inside 
the `content` property will also be displayed inside this 580 pixels wide column.

## Example input
The JSON code below would give you an email with a gray (body) background, 
and a content section with a yellow background. 

```javascript
{
    "from" : "info@example.com",
    "subject" : "Example email",
    "background" : {
        "color" : "#eee"
    },
    "content" : {
        "background" : {
            "color" : "yellow"
        },
        "blocks" : [ {
            "type": "image",
            "src": "http://www.responsiveemail.com/Resources/Images/responsive-email-logo.png"
        }, {
            "type": "text",
            "content": "Lorem ipsum dolor sit amet consectetur adipiscing elit, sed do eiusmod tempor incididunt ... mollit anim id est laborum."
        } ]
    }
}
```

## Example output

![](copernica-docs:ResponsiveEmail/images/example-output-content.png)

## Sub properties

As described above, and as demonstrated in the example JSON, the `content`
property is a nested property that can have different kind of sub properties.
The following table lists all sub properties that can be used inside the `content` 
section.

### Content block properties

| Property | Value | Description                                                                                         |
|:-----------------------------------------------------------------------------------------------------------------------|
| [background](/support/json/property-background) | _object_ | Background properties for the 580px wide center column.   |
| [blocks](/support/json/property-blocks) | _array_ | List of the actual content blocks inside the center column.        |
| [css](/support/json/property-css) | _object_ | Optional additional CSS properties to be added to the column.           |
| [attributes](/support/json/property-attributes) | _object_ | Optional additional attributes to be added to the column. |

## A word of warning about setting attributes and css

The 580 pixels wide central content section is implemented as a HTML table. 
Normally, you do not want to mess with this and add your own attributes or css 
properties to this table. However, the responsive API does support the nested 
`css` and `attributes` properties to adjust the table. So if you insist, you may 
modify the table styling, but we cannot guarantee that such changes will end up 
correctly in email clients.