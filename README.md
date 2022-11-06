# SSH Remote Command Action
A github action to execute command on remote server with SSH

# Usage
```
name: ssh command
on: push
jobs:
  ssh:
    runs-on: ubuntu-latest
    steps:
      - name: Configure and execute remote command
        uses: mnival/ssh-remote-commands-action@v0.0.1
        id: ssh
        with:
          ssh_host: ${{ secrets.SSH_HOST }}
          ssh_user: ${{ secrets.SSH_USER }}
          ssh_key: ${{ secrets.SSH_KEY }}
          ssh_commands: |
            echo "Test first line"
            echo "Line two"

      - name: Execute directly with alias provide in first action
        uses: mnival/ssh-remote-commands-action@v0.0.1
        with:
          ssh_host_alias: ${{ steps.ssh.outputs.ssh_host_alias }}
          ssh_commands: echo "Another action"
```
