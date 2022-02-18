### Sample Java Code



/*************************
 * @msgId: 12345678901234
 * @password: ORACLE1
 * @output: XBCxPH6C+cg=
 *************************/

private static String encryptPassword(String msgId, String password) throws Exception {

    MessageDigest mDigest = MessageDigest.getInstance(“SHA - 512”);
    byte[] digestSeed = mDigest.digest(msgId.getBytes());
    byte[] seedEncArray = Arrays.copyOf(digestSeed, 24);
    Cipher cipher = Cipher.getInstance(“DESede / CBC / PKCS5Padding”);
    SecretKeySpec skspec = new SecretKeySpec(seedEncArray, “DESede”);
    IvParameterSpec iv = new IvParameterSpec(new byte[8]);
    cipher.init(Cipher.ENCRYPT_MODE, skspec, iv);
    byte[] finalByteArray = cipher.doFinal(password.getBytes());
    String finalValue = new String(Base64.encodeBase64(finalByteArray));
    return finalValue;

}
