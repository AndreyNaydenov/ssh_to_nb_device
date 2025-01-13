## Objective:
Create a script to perform the following tasks:

1. **Retrieve Device Information**  
   Fetch device details from NetBox.
2. **Select Device**  
   Display the retrieved devices using `fzf` (a command-line fuzzy finder) for easy selection.
3. **Fetch Credentials**  
   Access the corresponding credentials for the selected device from Bitwarden.
4. **Select Credential**  
   Use `fzf` to display and choose the appropriate credential from the retrieved list.
5. **Connect via SSH**  
   Establish an SSH connection to the selected host through a jump host, using the chosen credentials (password-based authentication).

## Dependencies:

- sshpass - to use SSH interactive password in non-interactive manner
- bitwarden-cli - to get passwords
- jq - to get credential names from BitWarden
- nbcli - to get list of devices and addresses
- fzf - to provide choose interface for user
- ssh - to connect
- NOC host as a jumphost

## Install:

0. make sure that you have jq, bw, sshpass, fzf and python3 installed
1. make python venv ```python3 -m venv venv```
2. activate venv ```. ./venv/bin/activate```
3. install requirements ```pip install -r requirements.txt```
4. run ```nbcli init```
5. edit pynetbox 'url' and 'token' entries in user_config.yml: ~/.nbcli/user_config.yml
6. unlock BW vault ```bw unlock``` and export BW_SESSION key shell variable
7. make sure that you have "nbcli" and "sshdevicepass" in PATH (I have made softlinks to ~/.local/bin)
8. run ```sshdevicepass```

## TODO:

- Add nbcli results caching (call to nbcli takes a long time)
