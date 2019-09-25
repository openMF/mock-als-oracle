# mock-als-oracle

This app is a mock-pathfinder app. It can be used with the Mojaloop Account Lookup System (ALS) to store and retrieve parties by MSISDN. 

# Configuration

To Configure ALS to use this Oracle, you will submit a post request to the ALS Admin endpoint for Oracles (http://account-lookup-service-admin.local/oracles). The body of the request will be something like this:

  {
    "oracleIdType": "MSISDN",
    "endpoint": {
      "value": "http://<mock-als-oracle URL>/switch/oracles",
      "endpointType": "URL"
    },
    "currency": "USD",
    "isDefault": true
  }
  
# Create Party

To create a party, make a post request to http://<mock-als-oracle URL>/oracle/participants/MSISDN/<MSISDN of party>. The body of the request is:
  
  {
   "fspId": "<FSP Identifier>",
   "currency": "USD"
  }
  
# Retrieve Party by MSISDN

To retrieve a party (and this will be done automatically by ALS once the Oracle has been registered), submit a get request to: http://<mock-als-oracle URL>/oracle/participants/MSISDN/<MSISDN of party>. The mock-als-oracle will return the FSP ID and Currency for the party if it is found.
  
  
