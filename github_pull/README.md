# How To

- Create private key files under `github_pull/files/{{ github_user.name }}.id_rsa`
- Define username on one of these places
  - in `github_pull/files/map.jinja`
  - in pillar `pillar/github_user.sls` (can be any pillar file for the environment)

## map.jinja example
```
{% set github_repo = salt['grains.filter_by']({
    'Linux': {
        'username': 'my_user', 
        'fullname': 'github user',
        'mail': 'test@test.com',
        'group': 'my_group',
        'uid': 1001,
        'gid': 1001
    }
}, grain='kernel', merge=salt['pillar.get']('github_repo')) %}
```

## pillar example
```
github_repo:
    'username': 'my_user', 
    'fullname': 'github user',
    'mail': 'test@test.com',
    'group': 'my_group',
    'uid': 1001,
    'gid': 1001
```
