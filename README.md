# Operate license by using Rest API
This page introduces applications that use the EXPRESSCLUSTER REST API.  
For more information about each application, please see the README.md in the respective directory.  

You can get information and operate cluster and group resouces.  
In this case, you use RestAPI to operate the script and manage the license.

## Sample

1. Preparation
Install Node.js(v18 or higher.) and enable API in cluster properties.

2, Configuration

Create config.json as a configuration file, and specify your EXPRESSCLUSTER API server to "clpserver". Multiple servers can be monitored by writing multiple entries in "servers".  
Create sample.js

```
// Skip authorization
process.env.NODE_TLS_REJECT_UNAUTHORIZED = '0';

const authorizationBasic = 'Basic ' + btoa('<user>:<password>');

// request
const request = {
    method: 'GET',
    headers: {
        Authorization: authorizationBasic,
    },
};


// HTTP
fetch(
    'https://<server>:<port>/api/v1/servers',
    request,
).then(async (response) => {
    const data = (await response.json());
    console.log(`status: ${response.status}, json: ${JSON.stringify(data, null, 4)}`);
});
```

3. Run commands
```
> node sample.js
```
