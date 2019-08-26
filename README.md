# Cross-platform encription

I have to store sensitive data that cannot be stored without proper encryption. Some of this data is saved via PHP, some of it via Python.

Came up with this solution, basically AES-256-CBC with HMAC verification on both, Python and PHP, I'm not entirely sure if this is completly secure that's why I'm sharing it!

For python I've used PyCryptodome, for PHP openssl.
