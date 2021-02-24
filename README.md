# 1. Secret files

- [reference link (1)](https://git-secret.io/installation)
- [reference link (2)](https://nl.devoteam.com/en/blog-post/how-to-hide-your-secrets-in-a-git-repository-based-on-centos-7/)

#### Step 1.1: Install dependencies

```
brew install gnupg git-secret
```

- `NOTE: In case you faced permission with brew install try`:

```
sudo chown -R $(whoami) $(brew --prefix)/*
```

#### Step 1.2: Generate GPG key

```
gpg --full-generate-key
```

### Step 1.3: Send publickey to one of team member

```
gpg --export "key-registered-email@email.com" > <name>-publickey.asc
```

### Step 1.4: One of team member import key

```
gpg --import <name>-publickey.asc ; git secret tell key-registered-email@email.com
```

### Step 1.5: Working with git-secret

To reveal (decrypt) secret files

```
git secret reveal
```

Before commit new changes of secret files

```
git secret hide -d
```
