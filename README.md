# DomoticASW demo

A demo meant to easilly put your hands on DomoticASW.

The demo includes:

- DomoticASW web app
- An already configured domotic system with:
  - Users
  - Tasks and Automations
  - Users preferences about devices
  - Access control rules for users
- Simulated devices

Note that some devices are already registered to the system while others can be registered by you through automatic discovery.

## How to run it

```sh
docker compose up -d
```

The app will now be available at [localhost](http://localhost)

## How to stop it

```sh
docker compose down
```
