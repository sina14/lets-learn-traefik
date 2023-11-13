# lets-learn-traefik

## We're here to learn traefik together
![Traefik Image](traefik-logo.jpg)


## Docker Provider
 - 01-Basic: We're going to make hashicorp/vault accessible through traefik. the first example is very simple, you can connect to the address "vault.isc" using the HTTP protocol :white_check_mark:
 - 02-HTTPS: We'r going to use "websecure" entrypoint instead of "web" entrypoint to connect to "valut.isc" using HTTPS protocol . You have 3 different options to use tls in traefik . the first one is traefik default certifacte, the second one is using your own certificate and the last one is using let's encrypt. if you prefer to use let's encrypt, your provider must be supported by traefik, you can find the list of available providers here: https://doc.traefik.io/traefik/https/acme/ ✅
 - 03-RedirectScheme-middleware: The RedirectScheme middleware redirects the request if the request scheme is different from the configured scheme. We're going to redirect http requests to https using RedirectScheme middleware. https://doc.traefik.io/traefik/middlewares/http/redirectscheme/ ✅
 - 04-BasicAuth-middleware: The BasicAuth middleware grants access to services to authorized users only, because of that , We're going to create 2 different users. To create user:password pair, it's possible to use this command: echo $(htpasswd -nB user) | sed -e s/\\$/\\$\\$/g . you can use htpasswd if apache/httpd package is installed. https://doc.traefik.io/traefik/middlewares/http/basicauth/ ✅
 - 05-Errors-middleware: It has never been easier to say that something went wrong. The Errors middleware returns a custom page in lieu of the default, according to configured ranges of HTTP Status codes. In this example we're going to use a new service in our docker-compose called "error" . this new service is responsible to build Bunch of custom error pages for Traefik. you can follow their project here: https://github.com/guillaumebriday/traefik-custom-error-pages . so if i receive an error code (ex: 404) for my hashicorp/vault service , one of error pages of "error" service will be appeared based on status code. https://doc.traefik.io/traefik/middlewares/http/errorpages/ ✅
 - 06-Traefik-secure: We have been connecting to traefik dashboard in an insecure manner so far . we're going to connect to traefik dashboard using https protocol . because of that we need to follow some steps . first of all modify traefik.yml and replace "insecure:true" with "insecure:false" and then create a router for traefik service to enable tls using labels in docker-compose ✅

## Kubernetes IngressRoute Provider
  - 07-Setup: We're going to use traefik helm chart to install it. as i saild earlier, we have some different options to use tls in traefik . i'm using my own certificate for the examples of this repository. so i need to override some values of traefik helm chart. if you want to do the same, follow the steps in note.txt ✅
  - 08-Basic:
  - 09-HTTPS:
  - 10-RedirectScheme-middleware:
  - 11-BasicAuth-middleware:
