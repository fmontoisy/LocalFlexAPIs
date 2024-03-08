
# Introduction to LEM APIs
LEM provides a list of APIs to allow users’ applications to interact with the LEM platform. These APIs are an alternative to the user interface in place on LEM.

**Overview of the steps for FSPs**
The LEM platform allows FSPs to offer their flexibility to System operators, and to get rewarded when their offers get matched with a System Operator’s bid. There are 8 steps for the FSPs, which are briefly described here. Most of them can be performed both via the UI and the API.
1.	Register their organisation (UI only)
2.	Integrate their assets into LEM (UI or API)
3.	Fetch the System Operator bidding opportunities (UI or API)
4.	Offer their flexibility to System Operators (UI or API)
5.	Retrieve their contracts (UI or API)
6.	Dispatch their assets according to the contracts awarded (must be done by the FSP)
7.	Send their baselines to the LEM platform (UI or API)
8.	Submit their metering data to calculate their earnings (UI or API)

This document will focus only on the API capabilities. That is, for information on the user interface please refer to the general User Guide provided.

# Asset and Portfolio Management
Once an organisation is registered into LEM, its users can upload and manage their assets and portfolios on the platform via the following API endpoints:

## Create an asset
`POST` `/asset`: Create a new asset

**Requested body:**
```
{
  "assetType": "Aggregated",
  "name": "string",
  "siteMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "powerOutput": 0,
  "powerOutputUnit": "kW",
  "usabilityCapacity": 0,
  "usabilityCapacityUnit": "kWh",
  "minimumActivationTime": 0,
  "maximumActivationTime": 0,
  "responseTime": 0,
  "recoveryTime": 0,
  "canProvideMetering": true,
  "soApproved": true,
  "platformApproved": true,
  "powerOfAttorney": true,
  "rampRateUp": 0,
  "rampRateUpUnit": "kW/min",
  "rampRateDown": 0,
  "rampRateDownUnit": "kW/min"
}
```
**Responses:**

`200` successful operation
```
{
  "result": {
    "assetType": "Aggregated",
    "name": "string",
    "siteMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "powerOutput": 0,
    "powerOutputUnit": "kW",
    "usabilityCapacity": 0,
    "usabilityCapacityUnit": "kWh",
    "minimumActivationTime": 0,
    "maximumActivationTime": 0,
    "responseTime": 0,
    "recoveryTime": 0,
    "canProvideMetering": true,
    "soApproved": true,
    "platformApproved": true,
    "powerOfAttorney": true,
    "rampRateUp": 0,
    "rampRateUpUnit": "kW/min",
    "rampRateDown": 0,
    "rampRateDownUnit": "kW/min"
  },
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```
`403` You don't have have the permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```

## Update a single asset
`PATCH` `/asset/{MRID}`

**Requested body:**
```
{
  "assetType": "Aggregated",
  "name": "string",
  "siteMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "powerOutput": 0,
  "powerOutputUnit": "kW",
  "usabilityCapacity": 0,
  "usabilityCapacityUnit": "kWh",
  "minimumActivationTime": 0,
  "maximumActivationTime": 0,
  "responseTime": 0,
  "recoveryTime": 0,
  "canProvideMetering": true,
  "soApproved": true,
  "platformApproved": true,
  "powerOfAttorney": true,
  "rampRateUp": 0,
  "rampRateUpUnit": "kW/min",
  "rampRateDown": 0,
  "rampRateDownUnit": "kW/min"
}
```
**Responses:**

`200` successful operation
```
{
  "result": {
    "assetType": "Aggregated",
    "name": "string",
    "siteMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "powerOutput": 0,
    "powerOutputUnit": "kW",
    "usabilityCapacity": 0,
    "usabilityCapacityUnit": "kWh",
    "minimumActivationTime": 0,
    "maximumActivationTime": 0,
    "responseTime": 0,
    "recoveryTime": 0,
    "canProvideMetering": true,
    "soApproved": true,
    "platformApproved": true,
    "powerOfAttorney": true,
    "rampRateUp": 0,
    "rampRateUpUnit": "kW/min",
    "rampRateDown": 0,
    "rampRateDownUnit": "kW/min"
  },
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```

`403` You don't have permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```

## Return an asset
`GET` `/asset/{mrid}`: Return  a single asset

**Responses:**

`200` successful operation
```
{
  "result": {
    "assetType": "Aggregated",
    "name": "string",
    "siteMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "powerOutput": 0,
    "powerOutputUnit": "kW",
    "usabilityCapacity": 0,
    "usabilityCapacityUnit": "kWh",
    "minimumActivationTime": 0,
    "maximumActivationTime": 0,
    "responseTime": 0,
    "recoveryTime": 0,
    "canProvideMetering": true,
    "soApproved": true,
    "platformApproved": true,
    "powerOfAttorney": true,
    "rampRateUp": 0,
    "rampRateUpUnit": "kW/min",
    "rampRateDown": 0,
    "rampRateDownUnit": "kW/min"
  },
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```
`403` You don't have have the permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```


## Return all assets for a given site mrid
`GET` `/asset/portfolio{mrid}`: Return  a single asset

**Responses:**

`200` successful operation
```
{
  "result": [
    {
      "assetType": "Aggregated",
      "name": "string",
      "siteMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "powerOutput": 0,
      "powerOutputUnit": "kW",
      "usabilityCapacity": 0,
      "usabilityCapacityUnit": "kWh",
      "minimumActivationTime": 0,
      "maximumActivationTime": 0,
      "responseTime": 0,
      "recoveryTime": 0,
      "canProvideMetering": true,
      "soApproved": true,
      "platformApproved": true,
      "powerOfAttorney": true,
      "rampRateUp": 0,
      "rampRateUpUnit": "kW/min",
      "rampRateDown": 0,
      "rampRateDownUnit": "kW/min"
    }
  ],
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```
`403` You don't have have the permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```



## Create a portfolio
`POST` `/portfolio{mrid}`: create a portfolio

**Requested body:**
```
{
  "mrid": "string",
  "name": "string",
  "organisationMrid": "string",
  "marketRegionMrid": "string",
  "gridNodeMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "marketProducts": [
    "string"
  ]
}
```

**Responses:**

`200` successful operation
```
{
  "result": [
{
  "result": {
    "mrid": "string",
    "name": "string",
    "organisationMrid": "string",
    "marketRegionMrid": "string",
    "gridNodeMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "marketProducts": [
      "string"
    ]
  },
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```
`403` You don't have have the permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```


## Update a portfolio
`PATCH` `/portfolio{mrid}`: Update a single portfolio

**Requested body:**
```
{
  "mrid": "string",
  "name": "string",
  "organisationMrid": "string",
  "marketRegionMrid": "string",
  "gridNodeMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "marketProducts": [
    "string"
  ]
}
```

**Responses:**

`200` successful operation
```
{
  "result": [
{
  "result": {
    "mrid": "string",
    "name": "string",
    "organisationMrid": "string",
    "marketRegionMrid": "string",
    "gridNodeMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "marketProducts": [
      "string"
    ]
  },
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```
`403` You don't have have the permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```


## Delete a portfolio
`DELETE` `/portfolio{mrid}`: Delete a single portfolio

**Requested body:**
```
{
  "mrid": "string",
  "name": "string",
  "organisationMrid": "string",
  "marketRegionMrid": "string",
  "gridNodeMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "marketProducts": [
    "string"
  ]
}
```

**Responses:**

`200` successful operation
```
{
  "result": [
{
  "result": {
    "mrid": "string",
    "name": "string",
    "organisationMrid": "string",
    "marketRegionMrid": "string",
    "gridNodeMrid": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "marketProducts": [
      "string"
    ]
  },
  "status": true,
  "code": 200
}
```

`401` Access token is missing or invalid
```
{
  "result": "string",
  "status": true,
  "code": 401
}
```
`403` You don't have have the permission to access the response
```
{
  "result": "string",
  "status": true,
  "code": 403
}
```
