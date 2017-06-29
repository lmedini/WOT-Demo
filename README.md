# Demo for the WoT IG/WG F2F Meeting (9-13 July 2017 in Dusseldorf) PlugFest

# Things list
1. RFID Reader (http://www.lab-id.com/wordpress/wp-content/uploads/2016/03/KITNLO.pdf)
2. Display
3. REED
4. Multicolor LED

# Web Thing Descriptions

## RFID Reader

<pre class="example" title="More Capabilities">
{
  "@context": [
    "http://w3c.github.io/wot/w3c-wot-td-context.jsonld",
    { "actuator": "http://example.org/actuator#" }
  ],
  "@type": "Thing",
  "name": "MyLEDThing",
  "base": "coap://myled.example.com:5683/",
  "security": {
      "cat": "token:jwt",
      "alg": "HS256",
      "as": "https://authority-issuing.example.org"
    },
  "interactions": [
    {
      "@type": ["Property","actuator:onOffStatus"],
      "name": "status",
      "outputData": {"valueType": { "type": "boolean" }},
      "writable": true,
      "links": [{
        "href" : "pwr", 
        "mediaType": "application/exi" 
      },
      {
        "href" : "http://mytemp.example.com:8080/status",
        "mediaType": "application/json"
      }]
    },
    {
      "@type": ["Action","actuator:fadeIn"],
      "name": "fadeIn",
      "inputData": {
        "valueType": { "type": "integer" },
        "actuator:unit": "actuator:ms"
      },
      "links": [{
        "href" : "in", 
        "mediaType": "application/exi" 
      },
      {
        "href" : "http://mytemp.example.com:8080/in",
        "mediaType": "application/json"
      }]                  
    },
    {
      "@type": ["Action","actuator:fadeOut"],
      "name": "fadeOut",
      "inputData": {
        "valueType": { "type": "integer" },
        "actuator:unit": "actuator:ms"
      },
      "links": [{
        "href" : "out", 
        "mediaType": "application/exi" 
      },
      {
        "href" : "http://mytemp.example.com:8080/out",
        "mediaType": "application/json"
      }]                  
    },
    {
      "@type": ["Event","actuator:alert"],
      "name": "criticalCondition",
      "outputData": {"valueType": { "type": "string" }},
      "links": [{
              "href" : "ev",
              "mediaType": "application/exi"
            }]  
    }
  ]
}
    </pre>
