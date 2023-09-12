# Authentication

### HTTP Headers - All three HTTP Headers are mandatory for SOAP Services

 **Bearer Auth**:             
   type: http  
   scheme: bearer  
   bearerFormat: JWT          
   **name**: Authorization        
    
 **Api Key Auth**:              
   type: apiKey  
   in: header                 
   **name**: X-API-Key           
  
 **SOAP Action Auth**:         
   type: string  
   in: header                
   **name**: SOAPAction      
       

   

# Authorization

### Password Encryption [fcubs-encryption] - Data Element PASSWORD to be sent under FCUBS_HEADER element
Below is the process for FCUBS Password Encryption (sample code attached)


For Password encryption below logic should be used as per FCUBS:


1. MSGID, present as part of the FCUBS_HEADER in Request Payload, is considered as hash
2. External System should generate a unique Message ID (MSGID) with every request, which is functional mandatory field in the header.
3. Create a Message Digest with SHA-512 algorithm for the Message ID
4. The hash created from the previous step and the password in clear text together is encrypted in DESede encryption method. Recommended Padding PKCS5
5. Apply Base64 encoding to encrypted value and send under the PASSWORD data element under FCUBS_HEADER
