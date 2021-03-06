# Export an API from API Gateway<a name="api-gateway-export-api"></a>

 Once you created and configured an API in API Gateway, using the API Gateway console or otherwise, you can export it to a Swagger file using the API Gateway Export API, which is part of the Amazon API Gateway Control Service\. You have options to include the API Gateway integration extensions, as well as the [Postman](http://www.getpostman.com) extensions, in the exported Swagger definition file\. 

 You cannot export an API if its payloads are not of the `application/json` type\. If you try, you will get an error response stating that JSON body models are not found\. 

## Request to Export an API<a name="api-gateway-export-api-request"></a>

 With the Export API, you export an existing API by submitting a GET request, specifying the to\-be\-exported API as part of URL paths\. The request URL is of the following format: 

```
 https://<host>/restapis/<restapi_id>/stages/<stage_name>/exports/swagger
```

 You can append the `extensions` query string to specify whether to include API Gateway extensions \(with the `integration` value\) or Postman extensions \(with the `postman` value\)\. 

 In addition, you can set the `Accept` header to `application/json` or `application/yaml` to receive the API definition output in JSON or YAML format, respectively\. 

 For more information about submitting GET requests using the API Gateway Export API, see [Making HTTP Requests](https://docs.aws.amazon.com/apigateway/api-reference/making-http-requests)\. 

**Note**  
 If you define models in your API, they must be for the content type of "application/json" for API Gateway to export the model\. Otherwise, API Gateway throws an exception with the "Only found non\-JSON body models for \.\.\." error message\. 

## Download API Swagger Definition in JSON<a name="api-gateway-export-api-download-swagger-json"></a>

To export and download an API in Swagger definitions in JSON format:

```
GET /restapis/<restapi_id>/stages/<stage_name>/exports/swagger
Host: apigateway.<region>.amazonaws.com
Accept: application/json
```

 Here, `<region>` could be, for example, `us-east-1`\. For all the regions where API Gateway is available, see [Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#apigateway_region) 

## Download API Swagger Definition in YAML<a name="api-gateway-export-api-download-swagger-yaml"></a>

To export and download an API in Swagger definitions in YAML format:

```
GET /restapis/<restapi_id>/stages/<stage_name>/exports/swagger
Host: apigateway.<region>.amazonaws.com
Accept: application/yaml
```

## Download API Swagger Definition with Postman Extensions in JSON<a name="api-gateway-export-api-download-swagger-json-with-postman"></a>

To export and download an API in Swagger definitions with the Postman in JSON format:

```
GET /restapis/<restapi_id>/stages/<stage_name>/exports/swagger?extensions=postman
Host: apigateway.<region>.amazonaws.com
Accept: application/json
```

## Download API Swagger Definition with API Gateway Integration in YAML<a name="api-gateway-export-api-download-swagger-yaml-with-apig"></a>

To export and download an API in Swagger definitions with API Gateway integration in YAML format:

```
GET /restapis/<restapi_id>/stages/<stage_name>/exports/swagger?extensions=integrations
Host: apigateway.<region>.amazonaws.com
Accept: application/yaml
```

## Export API Using the API Gateway Console<a name="api-gateway-export-api-from-console"></a>

After [deploying your API to a stage](how-to-deploy-api-with-console.md), you can proceed to export the API in the stage to a Swagger file using the API Gateway console\.

 From the **stage configuration** page in the API Gateway console, choose the **Export** tab and then one of the available options \(**Export as Swagger**, **Export as Swagger \+ API Gateway Integrations** and **Export as Postman**\) to download your API's Swagger definition\. 

![\[Export API using the API Gateway console\]](http://docs.aws.amazon.com/apigateway/latest/developerguide/images/export-console.png)