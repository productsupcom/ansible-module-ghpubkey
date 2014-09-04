# ghpubkey
Adds or removes an SSH public key to a Github account

##Options

| parameter | required | default | choices | comments |
| --- | --- | --- | --- | --- |
| key | yes | | | The SSH public key, as a string |
| password | yes | | | Github account password |
| state | no | present	| present / absent | Whether the given key should or should not be added or not to the Github account |
| title | no | | | Title under which the Key will be known at Github |
| user | yes  | | | Github account username |

##Examples

```
# Add each SSH Public key collected in the Inventory sub-dir keys to Github
- ghpubkey: user={{github.username}} password={{github.password}} key="{{item}}" title="Ansible imported for {{ ansible_fqdn }}"
  with_file: "{{ inventory_dir }}/keys/{{ ansible_fqdn }}.pub"

# Add a single SSH Public Key using the Comment as a title
- ghpubkey: user={{github.username}} password={{github.password}} key="{{ssh_pub_key}}"
```

## License

```
The MIT License (MIT)

Copyright (c) 2014 Productsup GmbH, Yorick Terweijden yt@products-up.de

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```