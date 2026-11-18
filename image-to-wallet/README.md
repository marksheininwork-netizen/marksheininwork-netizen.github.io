# Image to Wallet

A browser-only tool that creates a signed Apple Wallet event pass from a chosen image.

## Privacy

The image, .p12 certificate, certificate password, and WWDR certificate are read locally in your browser. The signing key is never uploaded. The page loads JSZip and node-forge from jsDelivr; the site does not send your inputs to those libraries.

## Apple prerequisites

Apple requires a registered Pass Type ID and a matching Pass Type ID signing certificate. See Apple's account instructions: https://developer.apple.com/help/account/capabilities/create-wallet-identifiers-and-certificates/

You need a Pass Type ID beginning with pass., its matching Pass Type certificate exported as a password-protected .p12 file including the private key, your 10-character Apple Team ID, Apple's current WWDR intermediate certificate as .cer or .pem, and the .p12 export password.

## Use

Open the site on iPhone in Safari, choose an image, enter the Apple signing details, and create the pass. Tap the downloaded .pkpass file and add it to Wallet. The image is cropped to a wide banner for the event-ticket design.

## Deployment

This is a static site. Publish the image-to-wallet/ folder from the main branch of the GitHub Pages repository. The site requires HTTPS for Wallet pass installation.

## Technical notes

The page creates pass.json, image assets, a SHA-1 manifest, and a detached PKCS#7 signature, then packages them as a .pkpass. Signing material stays in browser memory and is cleared when the page is closed. A valid, current, matching Apple certificate is required for Wallet to accept the pass.
