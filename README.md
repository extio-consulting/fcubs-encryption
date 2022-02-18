# fcubs-encryption
Sample code(s) for FCUBS credentials Encryption


For Password encryption below logic should be used as per FCUBS:


1. MSGID, present as part of the FCUBS_HEADER in Request Payload, is considered as hash
2. External System should generate a unique Message ID (MSGID) with every request, which is functional mandatory field in the header.
3. Create a Message Digest with SHA-512 algorithm for the Message ID
4. The hash created from the previous step and the password in clear text together is encrypted in DESede encryption method. Recommended Padding PKCS5
5. Apply Base64 encoding to encrypted value and send under the PASSWORD data element under FCUBS_HEADER
