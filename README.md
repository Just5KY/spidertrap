# Spidertrap dockerized
Trap web crawlers and spiders in an infinite set of dynamically
generated webpages.

Install and run
---
`docker run --rm --name spidertrap -v .:/log/ -p 80:80 justsky/spidertrap`

OR

```yml
version "3"

services:
  spidertrap:
    name: spidertrap
    image: justsky/spidertrap
    restart: unless-stopped
    port:
      - 80:80
    volumes:
      - .:/log/
```

Then visit 127.0.0.1:80 in a web
browser. 

You should see a page containing randomly generated links. If
you click on a link it will take you to a page with more randomly
generated links.

Logs will be saved in spidertrap.log

```log
1.2.3.4 - - [21/May/2022 09:59:55] "GET /yf/XhuQwxZqdZwFG_6_U HTTP/1.1" 200 -
1.2.3.4 - - [21/May/2022 09:59:56] "GET /favicon.ico HTTP/1.1" 200 -
```

Trapping a Wget Spider
--------------------

`sudo wget -m http://127.0.0.1:80`

Wget will run until either it or Spidertrap is killed.

Build it yourself
---

- Clone this Repo
- Inside the repo, run this

 ```sh
 docker build -t spidertrap .
 ```

