# Version a template file, and ignore future changes.
Sometimes, you want to keep a file in your project history, but don't want to share senesitves data.
For exemple, you want to use a config file to define your DB access. This README wil show you how to do that.

# How to

You can create your config file :

```sh
nano connect.php
```

And fill it with your default content, and set the constants name but with empty values.

```php
<?php

define("DSN", "mysql:host=localhost;dbname=");
define("USER", "");
define("PASS", "");
```

If you check the versionning

```sh
git status

```
You can see the file is not followed yet but changes are detected.

```sh
Sur la branche master

Aucun commit

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)

	connect.php

aucune modification ajoutée à la validation mais des fichiers non suivis sont présents (utilisez "git add" pour les suivre)

```
As used, you can add it to the history

```shell
git add .
```
And commit it.

```shell
git commit -m "Add connect file template"
```
Now add the file to your list of ignored file by editing the .gitignore.

```shell
nano .gitignore
```

```shell
git add .
```

```shell
git commit -m "ignore connect"
```

fill the values of your configuration constants.

```shell
nano connect.php
```

With your sensitives data

```php
<?php
define("DSN", "mysql:host=localhost;dbname=checkpoint1");
define("USER", "root");
define("PASS", "jecode4wcs");
```

Then ignore last changes.

```shell
git update-index --assume-unchanged connect.php
```
look at the magic, if you check the versionning :

```shell
git status
```

You can see in the history git doesn't care about your `connect.php` file anymore !!

```sh
Sur la branche master
rien à valider, la copie de travail est propre
```

That's it ! Now you can continue developping your project with functionnal DB connection on local with no fear of sharing sensitive data.

And if a new developpeur start working on your projet he/she juste have to fill the blank but doesn't have to create from zero all the file.
