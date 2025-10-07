- SSL Certificates are small data files that digitally bind a
  cryptographic key to an organization\'s details. When installed on a
  web server, it activates the padlock and the https protocol and allows
  secure connections from a web server to a browser.

  1.  **Why do we need ssl?**

      SSL Certificates are small data files that digitally bind a
      cryptographic key to an organization\'s details. When installed on
      a web server, it activates the padlock and the https protocol and
      allows secure connections from a web server to a browser.

  2.  **How does it work?**

      Encryption Protects Data During Transmission. Web servers and web
      browsers rely on the Secure Sockets Layer (SSL) protocol to help
      users protect their data during transfer by creating a uniquely
      encrypted channel for private communications over the public
      Internet.

  - The following diagram tells us how SSL works :

    Here is a easyway to understand.Here Browser is client.

  - **Client:** "Hello there. I want to establish secure communication
    between the two of us. Here are my cipher suits and compatible
    SSL/TLS version."

  - **Server:** "Hello Client. I have checked your cipher suits and
    SSL/TLS version. I think we're good to go ahead. Here are my
    certificate file and my public key. Check 'em out."

  - **Client:** "Let me verify your certificate. (After a while) Okay,
    it seems fine, but I need to verify your private key. What I'll do
    is, I will generate and encrypt a pre-master (shared secret key) key
    using your public key. Decrypt it using your private key and we'll
    use thing master key to encrypt and decrypt the information"

  - **Server:** "Done."

    *\[Now that both the parties know who they're talking to, the
    information transferred between them will be secured using the
    master-key. Keep in mind that once the verification part is over,
    the encryption takes place through the master-key only. This is
    symmetric encryption.\]*

  - **Client:** "I'm sending you this sample message to verify that our
    master-key works. Send me the decrypted version of this message. If
    it works, our data is in safe hands."

  - **Server:** "Yeah, it works. I think we've accomplished what we were
    looking for."

\

-Nitin Raj
