# Adding CA Certificate to Trust Store

To prevent browser warnings about the self-signed certificate, you need to add the `rootCA.pem` file to your system's trust store. Follow the instructions below for your operating system:

## On macOS

1. Open Keychain Access.
2. Drag and drop the `rootCA.pem` file into the Keychain Access window.
3. Select the `System` keychain and set the certificate to "Always Trust".

## On Windows

1. Open the Certificate Manager by running `certmgr.msc`.
2. Go to the `Trusted Root Certification Authorities` store.
3. Import the `rootCA.pem` file into this store.

## On Linux

1. Copy the `rootCA.pem` file to the system's CA certificates directory, typically `/usr/local/share/ca-certificates/`:
    ```bash
    sudo cp rootCA.pem /usr/local/share/ca-certificates/
    ```
2. Update the CA certificates:
    ```bash
    sudo update-ca-certificates
    ```