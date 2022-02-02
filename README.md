 ansible role uguu
===================

This role installs [uguu](https://github.com/nokonoko/Uguu). Uguu is a simple lightweight temporary file hosting and sharing platform, but can also be used as a permanent file host

## Sample example of use in a playbook

The following code has been tested with Ubuntu 20.04

```yaml
 
- name: "install uguu"
  hosts: enter your hosts file
  beome: yes
  role:
    - ansible-role-uguu

  vars:
    git_release_version: v1.5.0
    max_upload_size: '128'
    paypalUrl: ""
    bitcoinAddress: ""
    siteName: name of your site
```
### Variables

These below variables are changeable. You can change these variables according to the description

| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `ubuntu_release` | `focal` | `Give your ubuntu release for add nginx repo` |
| `OnCalendar` | `*-*-* *:*:30` | `Define shell script running periodically. If change this shedule, give systemd OnCalendar time` |
| `uguu_release_version` | `v1.5.0` | `Give which release clone and install` |

### Front End
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `generateRobotstxt` | `false` | `I'd recommend making your own robots.txt` |
| `generateSitemap` | `false`| `Set as true for better SEO on e.g Google` |
| `max_upload_size` | `128` | `The max file size which an user can upload in MB` |
| `production` | `false` | `Set this to true when you're done tweaking` |
| `siteName` | `SITENAME` | `The name of your site. This will appear in the browser title and on several places on the website. If you changed the expire time remember to change that here as well` |
| `siteUrl` | `https://yoursite.com` | `Url to your site` |
| `abuseContact` | `abuse@example.com` | `The email dedicated to receive abuse reports, this can be the same as infoContact if you want. Make sure it's a valid email or else you run the risk of getting into trouble from your server provider` |
| `infoContact` | `info@example.com` | `The email dedicated to receive general email from users` |
| `ServerCountryLocation` | `Sweden` | `The country your server is located in, this is related to abuse/DMCA since it often depends on local laws` |
| `SiteMetaInfo` | `'{{ siteName }} is a temporary file hosting service, upload files up to 128MiB for24 hours'` | `A description of your site, search engines show this data in searches for your site` |

### Donations
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `paypalUrl` | `""` | `The URL to your Paypal donation page` |
| `bitcoinAddress` | `""` | `Your BTC address for donations` |
| `flattrUrl` | `""` | `Your Flattr donation URL` |

### Database and Upload File Store path
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `DB_PATH` | `'/var/www/db/uguu.sq3'` | `Path to your database` |
| `FILES_ROOT` | `'/var/www/files/'` | `The location where uploaded files are to be stored` |
| `URL` | `'{{ ansible_eth1.ipv4.address }}/files'` | `the URL of the subdomain serving the uploaded files, If you used single domain give that domain name or if you use localhost leave this default` |

### Misc
| variable name | default value | description |
| ------------- | ------------- | ----------- |
| `LOG_IP` | `'false'` | `You want you can turn this on and the IP of the uploaded file will be stored in the DB` | 
| `ANTI_DUPE` | `'false'` | `If enabled a file already uploaded won't be uploaded again` |
| `FILES_RETRIES` | `'15'` | `maximum number of tries to regenerate filename in case an existing one already exists, this is highly unlikely and even if it does 15 tries is more than enough` |
| `SSL` | `'false'` | `Set this to true if using HTTPS` |
| `NAME_LENGTH` | `'8'` | `The length of the new filename` |

## Contributing
Don't hesitate to create a pull request
