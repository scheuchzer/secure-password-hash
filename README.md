# secure-password-hash

Password Hash Class whith salt and PBKDF2WithHmacSHA1 enabled by default.

## Usage

Simply create a new instance of ``com.ja.security.PasswordHash``. The default configuration will do in most cases.

```java
@Test
public void testValidateCorrectPassword() throws Exception {
	String password = "My Test Password$";
	String correctHash = new PasswordHash().createHash(password);
	assertTrue(new PasswordHash().validatePassword(password, correctHash));
}
```

## Configuration
There are several setters for configuration. Alternatively you can pass in a ``Properties`` object to the ``configure`` method. Properties are as follows:

| Property                 | Default            | Description               |
|--------------------------|--------------------|---------------------------|
| hash-byte-size           | 24                 | the length of the hash to compute in bytes. Can be changed without breaking existing hashes. |
| salt-byte-size           | 24                 | the length of the salt to compute in bytes. Can be changed without breaking existing hashes. |
| pbkdf2-algorithm         | PBKDF2WithHmacSHA1 | the name of the pbkdf2 algorithm. Must be known to the  `javax.crypto.SecretKeyFactory` |
| pbkdf2-iterations        | 20000              | the iteration count (slowness factor). Can be changed without breaking existing hashes. |
| secure-random-algorithm  | SHA1PRNG           | the name of the algorithm to generate a salt. Must be known to `java.security.SecureRandom`. Can be changed without breaking existing hashes. |

## Author

- Thomas Scheuchzer 
  - http://java-adventures.com
  - https://github.com/scheuchzer
