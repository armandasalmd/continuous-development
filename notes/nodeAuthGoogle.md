## Node auth with Google oAuth: part 1 (session based)

#### The problem

Comes with a number of obstacles:

1. It's a lot of work

    - Must store salted/ encrypted user password securely in database
    - Must help users reset their passwords when they forget
    - Have to write fullstack code

1. Your users have to create new account and remeber new login credentials

1. Someone can now steal your hashed passwords

#### The solution

You can set your site up so that any time a user wants to sign in, they get redirected to another site (eg. Google, Facebook, Github, Twitter, or many others), then that site can come back and say "Margaret? Yeah we know Margaret. She's cool." And boom, now you can log Margaret into your site without you EVER having to see or worry about her password.

#### Great tutorial links:

[Sample google login website](https://auth-barkausa.herokuapp.com/#)

1.  [Session based google auth](http://gregtrowbridge.com/node-authentication-with-google-oauth-part1-sessions/)
1.  [JWT based google auth](http://gregtrowbridge.com/node-authentication-with-google-oauth-part2-jwts/)
1.  [Intro to refresh tokens](https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/)
