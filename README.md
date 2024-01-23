# DOSA

1. mkdir ui
2. cd ui
3. npx create-react-app .


Enter the following command ssh-keygen -t ed25519 -C "ananthan.rajasekharan@gmail.com"

Provide key file location and password.

Next addd the ssh key file to the ssh agent. Run the agent using eval "$(ssh-agent -s)"

Then add the key ssh-add ~/.ssh/id_ed25519 provide the password given when generating the ssh key.

Now read the generated ssh key file using cat ~/.ssh/id_ed25519.pub

Finally select and copy the contents of the id_ed25519.pub file, and add it to github ssh key section