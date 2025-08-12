# DN42 configuration

This folder contains the BGP configuration of AS4242423706 on DN42.\
Please note, this is a side fun project, don't expect this to be actively maintained.

[Peer map](https://map.iedon.net/#4242423706) • [Route graph](https://routegraphs.highdef.network/asn/4242423706) • [Looking glass](https://lg-dn42.legodard.fr/summary/zur-1) • [Website](https://dn42.legodard.fr/)

## Bird

Running on `bird2`, all the files in bird folders can replace the `/etc/bird` folder except envfile.

## systemd

All the files in this folder, need to be copied to `/etc/systemd/system/`, then `systemctl daemon-reload` and `systemctl enable --now dn42-<peer/dummy>`.

## crontab

```
*/15 * * * * curl -sfSLR {-o,-z}/etc/bird/roa_dn42.conf https://dn42.burble.com/roa/dn42_roa_bird2_4.conf && birdc configure > /dev/null
*/15 * * * * curl -sfSLR {-o,-z}/etc/bird/roa_dn42_v6.conf https://dn42.burble.com/roa/dn42_roa_bird2_6.conf && birdc configure > /dev/null
```

## Credits

The bird configuration files are copied from [howto/Bird2](https://dn42.eu/howto/Bird2) from DN42 wiki.