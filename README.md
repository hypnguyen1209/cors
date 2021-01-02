# cors
Cloudflare CORS proxy in a worker.

Fork from: https://github.com/Zibri/cloudflare-cors-anywhere

CLOUDFLARE-CORS-ANYWHERE

Source:
https://github.com/hypnguyen1209/cors/

Demo:
https://cors.hypnguyen.workers.dev/

Deploy workers:
https://workers.cloudflare.com/

Example:
```javascript
fetch('https://cors.hypnguyen.workers.dev/?https://httpbin.org/post', {
  method: 'post',
  headers: {
    'x-foo': 'bar',
    'x-bar': 'foo',
    'x-cors-headers': JSON.stringify({
      // allows to send forbidden headers
      // https://developer.mozilla.org/en-US/docs/Glossary/Forbidden_header_name
      'cookies': 'x=123'
    }) 
  }
}).then(res => {
  // allows to read all headers (even forbidden headers like set-cookies)
  const headers = JSON.parse(res.headers.get('cors-received-headers'))
  console.log(headers)
  return res.json()
}).then(console.log)
```

Note:

All received headers are also returned in "cors-received-headers" header.

Note about the DEMO url:

Abuse (other than testing) of the demo will result in a ban.  
The demo accepts only fetch and xmlhttprequest.  
To create your own is very easy, you just need to set up a cloudflare account and upload the worker code.  

