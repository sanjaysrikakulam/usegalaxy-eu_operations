# Operations Manual for usegalaxy.eu

- [Custom Subdomain](./subdomains.md)
- [Update a Tool](https://github.com/usegalaxy-eu/usegalaxy-eu-tools)

Galaxy Admin:

- [Upgrade Procedures](./upgrade.md)
- [Rebasing when upstream gets backports](./rebasing.md)
- [Process Management](./procmgmt.md)


## Read-only Fridays

- **NO EXCEPTIONS**
- Do not merge things to the playbook repositories that will be auto-applied
- Do not do any manual systems administration
- Consider writing documentation or more test cases instead.

## Adding a User to Grafana

1. They should [login](https://stats.galaxyproject.eu) using GitHub auth.
    - Note that they must be a member of an [approved organisation](https://github.com/usegalaxy-eu/infrastructure-playbook/blob/39d5b7e86b4f45acba53adb965b11b63700327ad/group_vars/grafana.yml#L119).  (Note that this link is to a specific revision where I could be sure the line number was correct, please check against `master`)
2. (As an admin) Open [the user list](https://stats.galaxyproject.eu/admin/users/)
3. Find them and "edit"
4. Under "Organizations" type "Main" and select the main organisation that shows up, adding them as the appropriate role.

## Adjusting a Tool's Requirements (Increasing Memory / CPU)

1. Edit
2. PR is merged
3. Wait until the end of the hour, at which the playbook will run. You should be able to confirm this via [grafana](https://grafana.denbi.uni-freiburg.de/dashboard/db/galaxy?refresh=1m&panelId=39&fullscreen&orgId=1)

## (Re-)sending activation links

Some users do not get the activation email or are unable to find it. On request we can generate the link with the
following procedure:

```bash
cd /opt/galaxy/server/
. ../venv/bin/activate
python /data/gxmnt/galaxy-dist/scripts/activation_link.py -c ~/config/galaxy.ini -e <their email>
```

