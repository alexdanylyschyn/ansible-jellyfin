# Jellyfin
Ansible role to install and configure [Jellyfin](https://jellyfin.org/) on Debian.

## Role Variables and Defaults

User that Jellyfin runs as.
```yml
jellyfin_user: "jellyfin"
```
Skip restarting Jellyfin, even on config change.
```yml
jellyfin_skip_restart: false
```
Enable fail2ban integration for the Jellyfin login.
```yml
jellyfin_enable_fail2ban: false
```
Set these if you use custom ports for Jellyfin.
```yml
jellyfin_fail2ban_ports:
  - "80"
  - "443"
```
Configuration of fail2ban parameters. You probably want to tweak these according to your userbase and threadmodel.
```yml
jellyfin_fail2ban_maxretry: "3"
jellyfin_fail2ban_bantime: "6000"
jellyfin_fail2ban_findtime: "600"
```

Additional Jellyfin options as in [Main Configuration Options](https://jellyfin.org/docs/general/administration/configuration#main-configuration-options)
```yml
jellyfin_additional_opts: ""
```

  
Jellyfin Paths
```yml
jellyfin_restart_opt: "--restartpath=/usr/lib/jellyfin/restart.sh"
jellyfin_ffmpeg_opt: "--ffmpeg=/usr/lib/jellyfin-ffmpeg/ffmpeg"
jellyfin_web_opt: "--webdir=/usr/share/jellyfin/web"
```

  
Jellyfin Directories
```yml
jellyfin_cache_dir: "/var/cache/jellyfin"
jellyfin_log_dir: "/var/log/jellyfin"
jellyfin_config_dir: "/etc/jellyfin"
jellyfin_data_dir: "/var/lib/jellyfin"
```

  
## Example Playbook

```yml
- hosts: jellyfin-hosts
  roles:
    - sleepy-nols.jellyfin
```

## Out of Role Scope

- Initial configuration
  
You still need to do the initial configuration via the webinterface


## Contributing

Contributions are welcome, please write meaningfull commit messages :)

## License
GPLv3
