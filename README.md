UniFi Controller Compose
========================

<p align="center">
    <a href="https://github.com/users/PHLAK/sponsorship"><img src="https://img.shields.io/badge/Become_a-Sponsor-cc4195.svg?style=for-the-badge" alt="Become a Sponsor"></a>
    <a href="https://paypal.me/ChrisKankiewicz"><img src="https://img.shields.io/badge/Make_a-Donation-006bb6.svg?style=for-the-badge" alt="One-time Donation"></a>
</p>

---

Requirements
------------

  - [Docker](https://www.docker.com)
    - [Docker Compose](https://docs.docker.com/compose/)
  - [GNU Make](https://www.gnu.org/software/make/) (optional)

Installation
------------
  
  1. Clone the repository

         git clone https://github.com/PHLAK/unifi-controller-compose.git

  2. Initialize the configuration files

          make init

      or manually

         cp --verbose .skelleton/config/*.env config/
         cp --verbose .skelleton/.env .

  3. Set the environment variables in `.env`

  4. Set the application-specific environment variables by editing the files found in the `config` directory

  5. Place your `config.yaml` file and any additional configuration files in `volumes/config`

  6. Run `docker-compose config` to validate and confirm your configuration

  7. Run `docker-compose up -d` to start the containers

### Watchtower

Watchtower configuration is controlled through the environment variables set in
the `config/watchtower.env` file. Check out the [Watchtower documentation](https://containrrr.dev/watchtower/)
(specifically the [Arguments](https://containrrr.dev/watchtower/arguments/) page)
for more information on the available envionment variables and what they do.

Updating Containers
-------------------

This project includes [Watchtower](https://containrrr.dev/watchtower/) that will
periodically check for new images on a schedule and update containers if found.

To manually fetch updated images and update the running containers run

    docker-compose pull && docker-compose up -d

Default Port Reference
----------------------

| Service                | Port    | Protocol | 
| ---------------------- | ------- | -------- |
| Web Admin              | `8443`  | TCP      |
| STUN                   | `3478`  | UDP      |
| AP Discovery           | `10001` | UDP      |
| Device Communication   | `8080`  | TCP      |
| L2 Network Discovery   | `1900`  | UDP      |
| Guest Portal HTTPS     | `8843`  | TCP      |
| Guest Portal HTTP      | `8880`  | TCP      |
| Mobile Throughput Test | `6789`  | TCP      |
| Remote Syslog          | `5514`  | UDP      |
