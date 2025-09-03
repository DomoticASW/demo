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

> **Note that:**
>
> - some devices are already registered to the system while others can be registered by you through automatic discovery.
> - a base delay and a random delay have been artifically added in order to show that our system can handle that.

## How to run it

```sh
docker compose up -d
```

The app will now be available at [localhost](http://localhost)

> **Note:**
>
> You can optionally set a `PORT` environment variable to decide on which port to expose the website
>
> ```sh
> PORT=3000 docker compose up -d
> ```
>
> The app will be available at [localhost:3000](http://localhost:3000)

## How to stop it

```sh
# Will stop the containers without deleting anonymous volumes keeping your modifications
docker compose stop
# If you want to restart the system
docker compose up
```

## How to start back from sample data

```sh
# Will stop and remove containers and anonymous volumes
docker compose down
# If you want to restart the system
docker compose up
```

## Sample data explained

### Users already registered to the system

| User          | Email                   | Password |
| ------------- | ----------------------- | -------- |
| Alex Carter   | alex.carter@email.com   | password |
| Mia Fernandez | mia.fernandez@email.com | password |
| Emma Carter   | emma.carter@email.com   | password |
| Liam Carter   | liam.carter@email.com   | password |

### Users that required access to the system but were not yet accepted

> **Note:**
> You are free to try to accept them

| User         | Email                  | Password |
| ------------ | ---------------------- | -------- |
| Evelyn Moore | evelyn.moore@email.com | password |

### Permissions

If you login as Liam or Emma you will notice that they are not able to execute action on some devices and execute or edit most of the tasks/automations.

The reason is that the admin (Alex) knows his children really well and has carefully crafted rules
in order to avoid his children messing up the house.

## How to modify and persist sample data

You should run:

```sh
# UNIX shells
DUMP_DB=true docker compose up -d
```

```powershell
# Powershell
$env:DUMP_DB="true"; docker compose up -d
```

```cmd
REM Command Prompt
set "DUMP_DB=true" && docker compose up -d
```

Once you have modified the sample data just stop the containers:

```sh
docker compose down
```

Once MongoDB container has stopped you can check that the [dump](./dump) folder has changed:

```sh
git status
```

You can then commit those changes:

```sh
git add ./dump
git commit -m "modified sample data"
```
