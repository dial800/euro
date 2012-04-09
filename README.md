![Documentation](http://docs.dial800.com/images/roundtrip.png)

We know. You have two days to integrate with us. Don't worry, it's easy. We're here to help.

## How to submit data

* [if I am using PHP](#using-php)?
* [or C Sharp?](#using-c-sharp)
* [or Python?](#using-python)
* [or Ruby?](#using-ruby)

### Using PHP

```php
<?php

# 1. Generate Payload

$request = new HTTP_Request2('http://routing.dial800.com/roundtrip');
$request->setMethod(HTTP_Request2::METHOD_POST)
    ->setAuth('user','password', HTTP_Request2::AUTH_BASIC)
    ->setHeader('Content-type: application/euro')
    ->setBody(
        "<?xml version=\"1.0\" encoding=\"utf-8\" ?>\r\n" .
        "<Call xmlns=\"http://www.dial800.com/roundtrip/2011-07-15\r\n" .
        "      xmlns:euro=\"http://www.eurorscgedge.com/2011-08-03\">" .
        "<ANI>tel:3105555555</ANI>\r\n" .
        "<Target>tel:3109999999</Target>\r\n" . 
        "<CallStart>2011-07-15T01:02:03-08:00</CallStart>\r\n" .
        "<euro:TelesalesId>UMG</euro:TelesalesId>\r\n" .
        "<euro:ClientId>GRDE</euro:ClientId>\r\n" .
        "<euro:ProductCode>GDV3</euro:ProductCode>\r\n" .
        "<euro:ProductDescription>GRAVDEFY</euro:ProductDescription>\r\n" .
        "<euro:SourceCode>NNNN</euro:SourceCode>\r\n" .
        "<euro:StateCode>CA</euro:StateCode>\r\n" .
        "<euro:StationType>T</euro:StationType>\r\n" .
        "<euro:OrderCall>true</euro:OrderCall>\r\n" .
        "<euro:InquiryCall>false</euro:InquiryCall>\r\n" .
        "<euro:CustomerServiceCall>false</euro:CustomerServiceCall>\r\n" .
        "<euro:ReferralCall>false</euro:ReferralCall>\r\n" .
        "<euro:CreditCardsCall>true</euro:CreditCardsCall>\r\n" .
        "<euro:InfoOnlyCall>false</euro:InfoOnlyCall>\r\n" .
        "<euro:MaleCall>true</euro:MaleCall>\r\n" .
        "<euro:FemaleCall>false</euro:FemaleCall>\r\n" .
        "<euro:Counter1>10</euro:Counter1>\r\n" .
        "<euro:Counter2/>\r\n" .
        "<euro:Counter3/>\r\n" .
        "<euro:Counter4/>\r\n" .
        "<euro:Counter5/>\r\n" .
        "<euro:Counter6/>\r\n" .
        "<euro:Counter7/>\r\n" .
        "<euro:Counter8/>\r\n" .
        "<euro:Counter9/>\r\n" .
        "<euro:Counter10/>\r\n" .
        "<euro:Counter11/>\r\n" .
        "<euro:Counter12/>\r\n" .
        "<euro:Counter13/>\r\n" .
        "<euro:Counter14/>\r\n" .
        "<euro:Counter15/>\r\n" .
        "<euro:Counter16/>\r\n" .
        "<euro:Counter17/>\r\n" .
        "<euro:Counter18/>\r\n" .
        "<euro:Counter19/>\r\n" .
        "<euro:Counter20/>\r\n" .
        "<euro:TransactionDateTime>2011-08-03T00:00:00Z</euro:TransactionDateTime>\r\n" .
        "<euro:OrderId>OrderId</euro:OrderId>\r\n" .
        "<euro:DollarAmount>100.00</euro:DollarAmount>\r\n" .
        "<euro:EuroCompanyId>1</euro:EuroCompanyId>\r\n" .
        "</Call>"
    );

# 2. Submit

echo $request->send()->getBody();
?>
```

### Using C Sharp

```csharp
using System;
using System.IO;
using System.Net;
using System.Text;


namespace Dial800
{
    class Program
    {
        static void Main(string[] args)
        {
            byte[] postDataBytes;
            const string userName    = "user";
            const string password    = "password";
            const string contentType = "application/euro";
            const string postMethod  = "POST";
            const string postData    
            = @"<?xml version="1.0" encoding="utf-8" ?>
                <Call xmlns="http://www.dial800.com/roundtrip/2011-07-15"
                      xmlns:euro="http://www.eurorscgedge.com/2011-08-03">      
                    <ANI>tel:3105555555</ANI>
                    <Target>tel:3109999999</Target>
                    <CallStart>2011-07-15T01:02:03-08:00</CallStart>
                    <euro:TelesalesId>UMG</euro:TelesalesId>
                    <euro:ClientId>GRDE</euro:ClientId>
                    <euro:ProductCode>GDV3</euro:ProductCode>
                    <euro:ProductDescription>GRAVDEFY</euro:ProductDescription>
                    <euro:SourceCode>NNNN</euro:SourceCode>
                    <euro:StateCode>CA</euro:StateCode>
                    <euro:StationType>T</euro:StationType>
                    <euro:OrderCall>true</euro:OrderCall>
                    <euro:InquiryCall>false</euro:InquiryCall>
                    <euro:CustomerServiceCall>false</euro:CustomerServiceCall>
                    <euro:ReferralCall>false</euro:ReferralCall>
                    <euro:CreditCardsCall>true</euro:CreditCardsCall>
                    <euro:InfoOnlyCall>false</euro:InfoOnlyCall>
                    <euro:MaleCall>true</euro:MaleCall>
                    <euro:FemaleCall>false</euro:FemaleCall>
                    <euro:Counter1>10</euro:Counter1>
                    <euro:Counter2/>
                    <euro:Counter3/>
                    <euro:Counter4/>
                    <euro:Counter5/>
                    <euro:Counter6/>
                    <euro:Counter7/>
                    <euro:Counter8/>
                    <euro:Counter9/>
                    <euro:Counter10/>
                    <euro:Counter11/>
                    <euro:Counter12/>
                    <euro:Counter13/>
                    <euro:Counter14/>
                    <euro:Counter15/>
                    <euro:Counter16/>
                    <euro:Counter17/>
                    <euro:Counter18/>
                    <euro:Counter19/>
                    <euro:Counter20/>
                    <euro:TransactionDateTime>2011-08-03T00:00:00Z</euro:TransactionDateTime>
                    <euro:OrderId>OrderId</euro:OrderId>
                    <euro:DollarAmount>100.00</euro:DollarAmount>
                    <euro:EuroCompanyId>1</euro:EuroCompanyId>
                </Call>";

            const string uri = "http://roundtrip.dial800.com/roundtrip";

            postDataBytes = Encoding.UTF8.GetBytes( postData );

            var urlEndpoint = new Uri(uri);
            var request = WebRequest.Create( urlEndpoint ) as HttpWebRequest;

            request.Credentials   = new NetworkCredential( userName, password );
            request.Method        = postMethod;
            request.ContentType   = contentType;
            request.ContentLength = postDataBytes.Length;

            using(Stream postStream = request.GetRequestStream())
            {
                postStream.Write( postDataBytes, 0, postDataBytes.Length );
            }

            try
            {
                using ( HttpWebResponse response = request.GetResponse() as HttpWebResponse )
                {
                    var reader = new StreamReader( response.GetResponseStream() );
                    Console.WriteLine( reader.ReadToEnd() );
                }
            }
            catch (WebException ex)
            {
                if (ex.Response != null)
                {
                    using (HttpWebResponse errorResponse = (HttpWebResponse)ex.Response)
                    {
                        Console.WriteLine(
                            "The server returned '{0}' with the status code {1} ({2:d}).",
                            errorResponse.StatusDescription, errorResponse.StatusCode,
                            errorResponse.StatusCode);
                    }
                }
            }
            Console.ReadKey();
        }
    }
}
```

### Using Python

```python
from requests.auth import HTTPBasicAuth
payload = '''
<?xml version="1.0" encoding="utf-8" ?>
<Call xmlns="http://www.dial800.com/roundtrip/2011-07-15"
      xmlns:euro="http://www.eurorscgedge.com/2011-08-03">      
    <ANI>tel:3105555555</ANI>
    <Target>tel:3109999999</Target>
    <CallStart>2011-07-15T01:02:03-08:00</CallStart>
    <euro:TelesalesId>UMG</euro:TelesalesId>
    <euro:ClientId>GRDE</euro:ClientId>
    <euro:ProductCode>GDV3</euro:ProductCode>
    <euro:ProductDescription>GRAVDEFY</euro:ProductDescription>
    <euro:SourceCode>NNNN</euro:SourceCode>
    <euro:StateCode>CA</euro:StateCode>
    <euro:StationType>T</euro:StationType>
    <euro:OrderCall>true</euro:OrderCall>
    <euro:InquiryCall>false</euro:InquiryCall>
    <euro:CustomerServiceCall>false</euro:CustomerServiceCall>
    <euro:ReferralCall>false</euro:ReferralCall>
    <euro:CreditCardsCall>true</euro:CreditCardsCall>
    <euro:InfoOnlyCall>false</euro:InfoOnlyCall>
    <euro:MaleCall>true</euro:MaleCall>
    <euro:FemaleCall>false</euro:FemaleCall>
    <euro:Counter1>10</euro:Counter1>
    <euro:Counter2/>
    <euro:Counter3/>
    <euro:Counter4/>
    <euro:Counter5/>
    <euro:Counter6/>
    <euro:Counter7/>
    <euro:Counter8/>
    <euro:Counter9/>
    <euro:Counter10/>
    <euro:Counter11/>
    <euro:Counter12/>
    <euro:Counter13/>
    <euro:Counter14/>
    <euro:Counter15/>
    <euro:Counter16/>
    <euro:Counter17/>
    <euro:Counter18/>
    <euro:Counter19/>
    <euro:Counter20/>
    <euro:TransactionDateTime>2011-08-03T00:00:00Z</euro:TransactionDateTime>
    <euro:OrderId>OrderId</euro:OrderId>
    <euro:DollarAmount>100.00</euro:DollarAmount>
    <euro:EuroCompanyId>1</euro:EuroCompanyId>
</Call>
'''
r = request.post('http://routing.dial800.com/routing',
                 auth=HTTPBasicAuth('user','password'),
                 headers={'content-type': 'application/euro'},
                 data=payload)
```

### Using Ruby

```ruby
require "net/http"
require "uri"

uri = URI.parse("http://routing.dial800.com/routing")

http         = Net::HTTP.new(uri.host, uri.port)
request      = Net::HTTP::Post.new(uri.host,uri.port)
request.body = xml_string
request.basic_auth("user","password")
request.content_type = "application/euro"
response     = http.request(request)
```

## Reference

### Authentication

### POST

#### Request

```
POST /calls
Content-Type: application/euro
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Call xmlns="http://www.dial800.com/roundtrip/2011-07-15"
      xmlns:euro="http://www.eurorscgedge.com/2011-08-03">      
    <ANI>tel:3105555555</ANI>
    <Target>tel:3109999999</Target>
    <CallStart>2011-07-15T01:02:03-08:00</CallStart>
    <euro:TelesalesId>UMG</euro:TelesalesId>
    <euro:ClientId>GRDE</euro:ClientId>
    <euro:ProductCode>GDV3</euro:ProductCode>
    <euro:ProductDescription>GRAVDEFY</euro:ProductDescription>
    <euro:SourceCode>NNNN</euro:SourceCode>
    <euro:StateCode>CA</euro:StateCode>
    <euro:StationType>T</euro:StationType>
    <euro:OrderCall>true</euro:OrderCall>
    <euro:InquiryCall>false</euro:InquiryCall>
    <euro:CustomerServiceCall>false</euro:CustomerServiceCall>
    <euro:ReferralCall>false</euro:ReferralCall>
    <euro:CreditCardsCall>true</euro:CreditCardsCall>
    <euro:InfoOnlyCall>false</euro:InfoOnlyCall>
    <euro:MaleCall>true</euro:MaleCall>
    <euro:FemaleCall>false</euro:FemaleCall>
    <euro:Counter1>10</euro:Counter1>
    <euro:Counter2/>
    <euro:Counter3/>
    <euro:Counter4/>
    <euro:Counter5/>
    <euro:Counter6/>
    <euro:Counter7/>
    <euro:Counter8/>
    <euro:Counter9/>
    <euro:Counter10/>
    <euro:Counter11/>
    <euro:Counter12/>
    <euro:Counter13/>
    <euro:Counter14/>
    <euro:Counter15/>
    <euro:Counter16/>
    <euro:Counter17/>
    <euro:Counter18/>
    <euro:Counter19/>
    <euro:Counter20/>
    <euro:TransactionDateTime>2011-08-03T00:00:00Z</euro:TransactionDateTime>
    <euro:OrderId>OrderId</euro:OrderId>
    <euro:DollarAmount>100.00</euro:DollarAmount>
    <euro:EuroCompanyId>1</euro:EuroCompanyId>
</Call>
```

#### Response

Call successfully matched.

```xml
200 OK
<ID>XDhshURwv60Q2nRyN4cnGVCmMB1cP</ID>
```

No match for the call.

```
404 Not Found
```

### PUT

```
PUT /calls
Content-Type: application/euro
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Call xmlns="http://www.dial800.com/roundtrip/2011-07-15"
      xmlns:euro="http://www.eurorscgedge.com/2011-08-03">      
    <ID>12345678990</ID>
    <euro:TelesalesId>UMG</euro:TelesalesId>
    <euro:ClientId>GRDE</euro:ClientId>
    <euro:ProductCode>GDV3</euro:ProductCode>
    <euro:ProductDescription>GRAVDEFY</euro:ProductDescription>
    <euro:SourceCode>NNNN</euro:SourceCode>
    <euro:StateCode>CA</euro:StateCode>
    <euro:StationType>T</euro:StationType>
    <euro:OrderCall>true</euro:OrderCall>
    <euro:InquiryCall>false</euro:InquiryCall>
    <euro:CustomerServiceCall>false</euro:CustomerServiceCall>
    <euro:ReferralCall>false</euro:ReferralCall>
    <euro:CreditCardsCall>true</euro:CreditCardsCall>
    <euro:InfoOnlyCall>false</euro:InfoOnlyCall>
    <euro:MaleCall>true</euro:MaleCall>
    <euro:FemaleCall>false</euro:FemaleCall>
    <euro:Counter1>10</euro:Counter1>
    <euro:Counter2/>
    <euro:Counter3/>
    <euro:Counter4/>
    <euro:Counter5/>
    <euro:Counter6/>
    <euro:Counter7/>
    <euro:Counter8/>
    <euro:Counter9/>
    <euro:Counter10/>
    <euro:Counter11/>
    <euro:Counter12/>
    <euro:Counter13/>
    <euro:Counter14/>
    <euro:Counter15/>
    <euro:Counter16/>
    <euro:Counter17/>
    <euro:Counter18/>
    <euro:Counter19/>
    <euro:Counter20/>
    <euro:TransactionDateTime>2011-08-03T00:00:00Z</euro:TransactionDateTime>
    <euro:OrderId>OrderId</euro:OrderId>
    <euro:DollarAmount>100.00</euro:DollarAmount>
    <euro:EuroCompanyId>1</euro:EuroCompanyId>
</Call>
```

#### Response

Call successfully matched.

```xml
200 OK
<ID>XDhshURwv60Q2nRyN4cnGVCmMB1cP</ID>
```

No match for the call.

```
404 Not Found
```

## Glossary
<dl>
    <dt>ID</dt>
    <dd>String value representing the alphanumeric Call ID of the phone call to be matched for the associated Sales data. Optional.<br/>
    (The “&lt;ID&gt;” element must always be passed on its own or an error will be issued.)
    </dd>
    <dt>DNIS</dt>
    <dd>10-Digit string value representing the DNIS (TFN) of the phone call to be matched for the associated Sales data. Optional.<br/>
    (The "&lt;DNIS&gt;" element must be passed if the “&lt;ID&gt;” element is absent.)</dd>
    <dt>ANI</dt>
    <dd>10-Digit string value representing the ANI (Caller #) of the phone call to be matched for the associated Sales data. Optional.<br/>
    (The "&lt;ANI&gt;" element must be passed if the “&lt;ID&gt;” element is absent.)</dd>
    <dt>Target</dt>
    <dd>10-Digit string value representing the Target (“RingTo”) number of the phone call to be matched for the associated Sales data. Optional.<br/>
    (The "&lt;Target&gt;" element must be passed if the “&lt;ID&gt;” element is absent.)</dd>
    <dt>CallStart</dt>
    <dd>The Call Start Time representing when this call was initiated. This value must be expressed using the standard XML DateTime format which includes the timezone offset identifier(i.e. “YYYY-MM-DDThh:mm:ss±HH:MM” or “YYYY-MM-DDThh:mm:ssZ”). Optional.<br/>
    (The "&lt;CallStart&gt;" element may optionally be passed if the “&lt;ID&gt;” element is absent.)</dd>
</dl>

## Working with Media Agencies

### MercuryMedia

[MercuryMedia](www.mercurymedia.com) uses two slightly different formats, [MLF](http://docs.dial800.com/dial800/mlf) and [MSF](http://docs.dial800.com/dial800/msf).

## Other Integrations

### Dial800

[Our native interface](http://docs.dial800.com/).

### Omni

Working with Omni? You can find more details [here](https://github.com/dial800/omni}).