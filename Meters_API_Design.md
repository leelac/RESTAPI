## Meters Collection [/meters]
Meters endpoint allows you to list or view all the meters of the logged in/anonymous customer or to POST/Validate the meter details. Responses from this endpoint will be retuned in JSON format only.

#### Meter
Meter as a resource represents following information

| Property | Type | As request | As response | Description |
| :-------------------- | :---------- | :---------- | :---------- | ------------------------------------------------------------ |
| businessPartnerNumberCP | string | `Mandatory` | `Returned always` |  It is a unique identifier. |
| contractAccountNumber  | string | `Mandatory` | `Returned always` |  Indicates the contractAccountNumber or collective contract account number |
| mpan | string | `Optional` | `Returned always` |  Meter point identifier (MPAN) of the meter, if available for search. |
| mprn | string | `Optional` | `Returned always` |  Meter point identifier (MPRN) of the meter, if available for search. |
| siteAddressPostCode | string | `Optional` | `Returned always` |  Site address post code,if available for search. |
| brokerBusinessPartnerNumberCP | string | `Optional` | `Returned always` |  Broker bpcp value,if available. |
| brokerBusinessOrgNumber | string | `Optional` | `Returned always` |  Broker bporg value,if available. |
| validateOrPost | string | `Optional` | `Returned always` |  For validation ‘V’, For post ‘P’, if available. |
| email | string | `Optional` | `Returned always` |  email address to be given for getting email. |
| numberOfMeters | String | `Mandatory` | `Returned always` |  Number of meters available. |
| subMeters | Array of subMeters | `Mandatory` | `Returned always` |  Sub meter details associated. |


#### Submeter
Submeter as a resource represents following information

| Property | Type | As request | As response | Description |
| :-------------------- | :---------- | :---------- | :---------- | ------------------------------------------------------------ |
| equipmentNumber | string | `Optional` | `Returned always` |  Equipment number of the meter. |
| formattedSiteAddress | number | `Optional` | `Returned always` |  Formatted site address associated with the meter. |
| productType | string | `Optional` | `Returned always` |  Product type, gas or elec |
| billingType | string | `Optional` | `Returned always` |  Billing type, monthly or quarterly. |
| meterSerialNumber | string | `Optional` | `Returned always` |  Meter serial number of the meter. |
| registers | Array of Register | `Mandatory` | `Returned always` |  Registers associated with the meter. |

#### Register
Register as a resource represents following information

| Property | Type | As request | As response | Description |
| :-------------------- | :---------- | :---------- | :---------- | ------------------------------------------------------------ |
| lastMeterRead | string | `Optional` | `Returned always` |  Last meter read of a particular meter. |
| lastMeterReadDate | date | `Optional` | `Returned always` |  Last meter read date of a particular meter. |
| industryRegisterID | string | `Optional` | `Returned always` |  IndustryRegisterID, if available. |
| registerID | string | `Optional` | `Returned always` |  RegisterID, if available. |
| numberOfDials | string | `Optional` | `Returned always` |  Number of dials available. |
| readStatus | string | `Optional` | `Returned always` |  P for Plausible or I for Implausible. |
| lastReadType | string | `Optional` | `Returned always` |  LastReadType of a meter, expected values are Estimated Read or Actual Read. |
| readType | string | `Optional` | `Returned always` |  ReadType of a meter, expected values are Estimated Read or Actual Read. |
| registerType | string | `Optional` | `Returned always` |  registerType of a meter, expected values are 01 On-peak rate, 02 Off-peak rate. |
| meterRead | string | `Optional` | `Returned always` |  Meter read of a particular meter. |
| meterReadDate | date | `Optional` | `Returned always` |  Meter read date of a particular meter. |


### Retrieve All meters [GET /meters]

+ Request 'Retrieving meter details'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 200 (application/json)

            {
                "status": "SUCCESS",
                "data": {
                    "meters": [
                        {
                            "businessPartnerNumberCP": "2005277938",
                            "contractAccountNumber": "600000686",
                            "numberOfMeters": "3",
							"subMeters": [
                                {
                                    "equipmentNumber": "000000000010036660",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "01",
                                    "billingType": "Q",
                                    "meterSerialNumber": "5005937S",
									"registers": [
                                {
                                    "lastMeterRead": "7689",
                                    "lastMeterReadDate": "19/11/2016",
                                    "registerID": "03287",
                                    "numberOfDials": "04",
									"readStatus": "02",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ]
                        }
                    ]
                },
                "errors": {},
                "meta": {}
            }
            
+ Request 'Retrieving multiple meter details'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 200 (application/json)

          {
                "status": "SUCCESS",
                "data": {
                    "meters": [
                        {
                            "businessPartnerNumberCP": "2005277938",
                            "contractAccountNumber": "600000686",
                            "numberOfMeters": "3",
							"subMeters": [
                                {
                                    "equipmentNumber": "000000000010036660",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "01",
                                    "billingType": "Q",
                                    "meterSerialNumber": "5005937S",
									"registers": [
                                {
                                    "lastMeterRead": "7689",
                                    "lastMeterReadDate": "19/11/2016",
                                    "registerID": "03287",
                                    "numberOfDials": "04",
									"readStatus": "02",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ],
							"subMeters1": [
                                {
                                    "equipmentNumber": "000000000010036550",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "02",
                                    "billingType": "M",
                                    "meterSerialNumber": "4005937S",
									"registers": [
                                {
                                    "lastMeterRead": "1234",
                                    "lastMeterReadDate": "19/02/2017",
                                    "registerID": "03287",
                                    "numberOfDials": "05",
									"readStatus": "02",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ]
                        }
                    ]
                },
                "errors": {},
                "meta": {}
            }
            

+ Request 'Customer is not authenticated'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 401 (application/json)

            {
                "status": "FAIL",
                "data": {},
                "errors": [
                    {
                        "code": "authorize",
                        "message": "invalid_request"
                    }
                ],
                "meta": {}
            }

### Retrieve meter for specific accounts [GET /meters{?account*}]
+ Parameters

  + account: 600000686 (string) - This is the customers account number

+ Request 'SUCCESS'

    + Headers

            Authorization: Bearer accesstoken
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 200 (application/json)

                        {
                "status": "SUCCESS",
                "data": {
                    "meters": [
                        {
                            "businessPartnerNumberCP": "2005277938",
                            "contractAccountNumber": "600000686",
                            "numberOfMeters": "3",
							"subMeters": [
                                {
                                    "equipmentNumber": "000000000010036660",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "01",
                                    "billingType": "Q",
                                    "meterSerialNumber": "5005937S",
									"registers": [
                                {
                                    "lastMeterRead": "7689",
                                    "lastMeterReadDate": "19/11/2016",
                                    "registerID": "03287",
                                    "numberOfDials": "04",
									"readStatus": "02",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ]
                        }
                    ]
                },
                "errors": {},
                "meta": {}
            }

+ Request 'Account number is invalid'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 400 (application/json)

          {
              "status": "FAIL",
              "data": {},
              "errors": [
                  {
                      "code": "account",
                      "message": "error.bgbusiness.account.number.invalid"
                  }
              ],
              "meta": {}
          }

+ Request 'Account is not available for the customer'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 403 (application/json)

          {
              "status": "FAIL",
              "data": {},
              "errors": [
                  {
                    "code": "account",
                    "message": "error.bgbusiness.account.not.match"

                  }
              ],
              "meta": {}
          }

### Retrieve meters using MPXN [GET /meters{?mpxn*}]
+ Parameters

  + mpxn: 1343152901 (string, required) - MPAN/MPRN of the meter, if available.

+ Request 'SUCCESS'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 200 (application/json)

            {
                "status": "SUCCESS",
                "data": {
                    "meters": [
                        {
                            "businessPartnerNumberCP": "2005277938",
                            "contractAccountNumber": "600000686",
                            "numberOfMeters": "3",
							"mpan": "1343152901",
							"subMeters": [
                                {
                                    "equipmentNumber": "000000000010036660",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "01",
                                    "billingType": "Q",
                                    "meterSerialNumber": "5005937S",
									"registers": [
                                {
                                    "lastMeterRead": "7689",
                                    "lastMeterReadDate": "19/11/2016",
                                    "registerID": "03287",
                                    "numberOfDials": "04",
									"readStatus": "02",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ]
                        }
                    ]
                },
                "errors": {},
                "meta": {}
            }

+ Request 'Meter is not available for the customer'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 404 (application/json)

          {
              "status": "FAIL",
              "data": {},
              "errors": [
                  {
                       "code": "meter",
                      "message": "error.bgbusiness.meter.details.notFound"

                  }
              ],
              "meta": {}
          }

### Post Meter Details [POST /meters]

+ Request 'Posting meter details'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 200 (application/json)

            {
                "status": "SUCCESS",
                "data": {
                    "meters": [
                        {
                            "businessPartnerNumberCP": "2005277938",
                            "contractAccountNumber": "600000686",
                            "numberOfMeters": "3",
							"validateOrPost": "P",
							"subMeters": [
                                {
                                    "equipmentNumber": "000000000010036660",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "01",
                                    "billingType": "Q",
                                    "meterSerialNumber": "5005937S",
									"registers": [
                                {
                                    "lastMeterRead": "7689",
                                    "lastMeterReadDate": "19/11/2016",
									"meterRead": "1234",
                                    "meterReadDate": "19/11/2016",
                                    "registerID": "03287",
                                    "numberOfDials": "04",
									"readStatus": "P",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ]
                        }
                    ]
                },
                "errors": {},
                "meta": {}
            }

### Validate Meter Details [POST /meters]

+ Request 'Validating meter details'

    + Headers

            Authorization: Bearer {accesstoken}
            cid: 05e230bf-a9cf-4b31-bc54-d3a995f62526

+ Response 200 (application/json)

            {
                "status": "SUCCESS",
                "data": {
                    "meters": [
                        {
                            "businessPartnerNumberCP": "2005277938",
                            "contractAccountNumber": "600000686",
                            "numberOfMeters": "3",
							"validateOrPost": "V",
							"subMeters": [
                                {
                                    "equipmentNumber": "000000000010036660",
                                    "formattedSiteAddress": "4, Shaftesbury Road, CRAWLEY, RH10 7HD",
                                    "productType": "01",
                                    "billingType": "Q",
                                    "meterSerialNumber": "5005937S",
									"registers": [
                                {
                                    "lastMeterRead": "7689",
                                    "lastMeterReadDate": "19/11/2016",
									"meterRead": "1234",
                                    "meterReadDate": "19/11/2016",
                                    "registerID": "03287",
                                    "numberOfDials": "04",
									"readStatus": "P",
                                    "lastReadType": "CO"
                                }
                            ]
                                }
                            ]
                        }
                    ]
                },
                "errors": {},
                "meta": {}
            }
