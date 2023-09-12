# Authentication

### HTTP Headers

 **Bearer Auth**:             # arbitrary name for the security scheme  
   type: http  
   scheme: bearer  
   bearerFormat: JWT          # optional, arbitrary value for documentation purposes  
   name: Authorization  
    
 **Api Key Auth**:              # arbitrary name for the security scheme  
   type: apiKey  
   in: header                 # can be "header", "query" or "cookie"  
   name: X-API-Key            # name of the header  
  
 **SOAP Action Auth**:          # arbitrary name for the security scheme  
   type: string  
   in: header                 # should be "header" with key "SOAPAction" and value for it as shared with the Endpoint for each SOAP Operation  
   name: SOAPAction           # name of the header, query parameter or cookie    
       

   

# Authorization

### Password Encryptiuon [fcubs-encryption]
Sample code(s) for FCUBS Password Encryption


For Password encryption below logic should be used as per FCUBS:


1. MSGID, present as part of the FCUBS_HEADER in Request Payload, is considered as hash
2. External System should generate a unique Message ID (MSGID) with every request, which is functional mandatory field in the header.
3. Create a Message Digest with SHA-512 algorithm for the Message ID
4. The hash created from the previous step and the password in clear text together is encrypted in DESede encryption method. Recommended Padding PKCS5
5. Apply Base64 encoding to encrypted value and send under the PASSWORD data element under FCUBS_HEADER
