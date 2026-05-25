#todo 

- [x] We have lost wireguard access. wg-easy doesn't work out of the box anymore. what to do, what to do... -> fixed

- [x] After fixing stuff, setup ufw, see if we can still make it work. Then check if other containers can still work, -> acutally setup nginx, and block all expect for incoming nginx requests.

- [x] Also clean up other containers, e.g. see if it makes sense to have containers use 'network_most: host', like home_assistant. -> looks good, updated wg-easy a bit to use PASSWORD_HASH