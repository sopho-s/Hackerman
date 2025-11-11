json web tokens are a way of letting the client store session details, these will then get transmitted each time and the payload can then be extracted, while the jwt does use signing to confirm that the details transmitted are correct, some of the time the developers will forget to authenticate this signature against the payload, which results in the user being able to modify the payload without the server knowing
# Sensitive data disclosure
the first common mistake is putting important credentials within a jwt, instead, the developer should store the values server side and use a lookup table instead to retrieve the data
# Not verifying signatures
If the server does not verify the signature of the jwt, then it is possible to modify the claims in the jwt to whatever you prefer them to be
# Downgrading to none
another common issue is a signature algorithm downgrade. JWTs support the `None` signing algorithm, which effectively means no signature is used with the JWT. This is intended for server-to-server communication
# Weak symmetric secrets
the security of JWT relies on the strength and entropy of the secret used. If a weak secret is used, it may be possible to perform offline cracking to recover the secret
# Signature algorithm confusion
similar to downgrading to none, when jwt uses an asymmetric signing algorithm for example RS256, it may be possible to downgrade to HS256. In these cases you could use the public key to forge a valid signature using the HS256 algorithm
# Audience claim
some JWTs may be issued by a single authentication server, this authentication server will issue the JWT to the user for a specific application they are trying to use, if this is not validated by the application they are using, they could use a JWT for one application on another application