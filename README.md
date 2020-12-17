# Clojure Lib Deployer
A simple "Clojure library deployer" written in Babashka

## Usage

Configure your CI as normal. Then, export your GPG keys:

```bash
# To export the "owner trust":
gpg --export-ownertrust  | base64 --wrap=0
# To export the "secret key":
gpg --export-secret-keys  | base64 --wrap=0
```

Then export these two base64-encoded elements into vars `GPG_OWNERTRUST` and `GPG_SECRET_KEYS`, in this order. Then, find how your CI exposes tags, 
and export the tag name as `TAG`:

```bash
# To expose CircleCI tag:
export TAG=$CIRCLE_TAG
```

Finally, get the current deployer for your tool and use it:

```bash
# If your project uses lein:
curl https://raw.githubusercontent.com/mauricioszabo/clj-lib-deployer/master/deploy-lein.bb -o deploy
curl -L  https://github.com/borkdude/babashka/releases/download/v0.2.5/babashka-0.2.5-linux-amd64.zip -o bb.zip
unzip bb.zip
sudo mv bb /usr/bin
chmod +x deploy
./deploy
```
