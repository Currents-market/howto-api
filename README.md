# howto-api
A repository for using Currents.market's APIs

# API / Swagger Docs
* [Intergration](https://docs.svc.integration-421315.env.currents.tech/openapi.yaml) <-- CLICK HERE TO DOWNLOAD FOR INTEGRATION
  * Endpoint Root : https://api.integration.app.currents.market
* [Production](https://docs.api.app.currents.market/openapi.yaml) <-- CLICK HERE TO DOWNLOAD FOR PRODUCTION
  * Endpoint Root : https://api.currents.market

For easy viewing, download one of the API docs and "load" it into [this WYSIWYG editor](https://editor-next.swagger.io/).  We'll soon have the ability to autoload the API docs directly into Swagger.

# How to use

## API Key

An API key is a shared secret between the customer and Currents.  It must be kept safe and private, and if it is exposed, you should notify Currents ASAP.

Currents uses the header `X-Api-Key` to designate the chosen API Key.

### Notes

System behavior is unpredictable if you attempt to use multiple AUTHZ mechanisms simultaenously.  Please use one at a time.

### Examples

Today, the `insight` service is functional on 2 end points :
* /insight/vin/{VIN}
* /insight/year/{YEAR}/make/{MAKE}/model/{MODEL}/variant/{VARIANT}

Remember to substitute your key in the following example :
```
curl -H 'X-Api-Key: ABCDEFGHIJKLMNOP' -O https://api.integration-421315.env.currents.tech/insight/vin/1N4AZ1BV3NC561510
```

This command yields something like : 
```
currents@market:~/Desktop/Projects/howto-api$ cat 1N4AZ1BV3NC561510 
{"YMMV":{"Year":2022,"Make":"Nissan","Model":"Leaf","Variant":"BEV","Drivetrain":"BEV"},"BatteryType":"Nissan Leaf Gen 4","Energy":"40.00","ChemistryType":"Lithium-Ion","CellChemistry":"NMC 532","EstimatedValue":"$235.34","Attributes":{"Battery Supplier":"AESC","Battery Thermal Management":"Air","Capacity (Ah)":"","Cell Energy Density (Wh/kg)":"","Cell Format":"Pouch","DOT Hazardous Materials Classification":"Hazardous","Dimensions":"1188 mm (46.77 in) x 264 mm (10.39 in) x 1547 mm (60.90 in)","Form Factor":"Pack","Nominal Voltage":"","Number of cells":"192","Number of modules":"24","Pack Energy Density (Wh/kg)":"","Total module weight":"","Weight (lbs)":"672.4"}}
```

The equivalent YMMV query is :
```
curl -H 'X-Api-Key: ABCDEFGHIJKLMNOP' https://api.integration.app.currents.market/insight/year/2022/make/nissan/model/leaf/variant/BEV
```

## Limits

API Users are PRO users and currently have no limits on total volume.  We will throttle requests as neccessary to keep the platform stable.

Please contact us if you run into issues.
