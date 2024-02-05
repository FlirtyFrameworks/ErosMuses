# WarpFusion <> Runpod

A relatively easy way to get it going without any additional costs (this method does not use Ngrok)

## Relevant Links

https://blog.runpod.io/how-to-set-up-terminal-access-on-runpod/

https://blog.runpod.io/how-to-connect-google-colab-to-runpod/

https://docs.runpod.io/docs/transfer-data

https://www.patreon.com/sxela/posts

https://github.com/Sxela/WarpFusion

## Instructions (Done on macOS, but should work for Linux and Windows with some minor tweaks)

1. Generate SSH keys (full article above)
    1. open Terminal 
    2. Enter the command: `**ssh-keygen -t ed25519**`
    3. Get your pub key with the command:  `**cat ~/.ssh/id_ed25519.pub**`
    4. Copy the output which will look something like this:  
    `**ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINN2938 zero@ZerosMac.lan**`
2. Add SSH public key to Runpod
    1. Login to Runpod
    2. Click Settings in the left menu
    3. Find and Click SSH Public Keys
    4. Paste the Pub Key output from the previous step, then click “Update Public Key”
3. Create Runpod instance - if using “Community Cloud” make sure you find a runtime that has a Public IP option.  You can filter at the top by checking “Public IP”

***Note*** According to Sxela’s patreon the minimum requirements are “16 gigs of RAM and an NVidia GPU with at least 8 gigs or VRAM”
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/afc25f42-3c4d-400f-bd08-9babcda812ae/Untitled.png)
    
    1. Use the Runpod Template - RunPod Pytorch 2.0.1
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e7a4e802-b674-48e7-90ff-54c1c992de34/Untitled.png)
        
    2. Click the “Customize Deployment” button
    3. Make sure you create enough space on both the container disk and volume disk.  
    
    ***NOTE*** The container disk only keeps data while the Runpod instance is active.  Once you terminate that instance all the data will be gone.  The Volume disk will store data even after you terminate the runtime.  The Volume disk will show up as the directory /workspace on the instance
    You can also setup a cloud storage sync with Dropbox, AWS, Google Cloud Storage (not Google Drive), etc.  This will sync your /workspace directory to the provider you choose.  Link is above with instructions how to set that up.
    4. Copy and Paste this Docker command into the deployment settings:
    
        
        <aside>
        💡 bash -c 'pip install --upgrade jupyter_http_over_ws>=0.0.7;jupyter serverextension enable --py jupyter_http_over_ws; cd /;conda install pytorch==2.0.0 torchvision==0.15.1 --index-url https://download.pytorch.org/whl/cu117 -c pytorch;apt-get update;apt-get install ffmpeg libsm6 libxext6 -y; ./start.sh'
        
        []()
        
        </aside>
        
        Like so…
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6b603336-1ca1-4678-958b-4fc7d6e756bf/Untitled.png)
        
4. Click “Set Overrides” then “Continue” 
5. Click “Deploy”
6. Find your new instance in “My Pods” and expand it
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/77e9e437-ac8e-4b39-83cd-8632990b8e59/Untitled.png)
    
7. Click Connect and copy the “SSH over exposed TCP” command
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1b920c73-f808-4010-aa50-a1b9568963d0/Untitled.png)
    
8. Paste the SSH command in a new Terminal window (or the one from before if it’s still open) and then you’ll need append `**-L 8888:localhost:8888**` 
So instead of this: ** `ssh [root@213.173.98.84](mailto:root@213.173.98.84) -p 54036 -i ~/.ssh/id_ed25519**`
You'll have this:  **`ssh [root@213.173.98.84](mailto:root@213.173.98.84) -p 54036 -i ~/.ssh/id_ed25519 -L 8888:localhost:8888`**
Press enter and it should connect to the server over SSH while also creating a tunnel on port 8888.  The first time it will likely ask you to confirm the connection.  Say yes.
Once connected you should see something like this with the “root@xxxxx” prompt…

    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4b1cbac9-bb77-41e3-bfda-38ec1865303b/Untitled.png)
    
9. Your tunnel is now connected!  Back to Runpod!
10. Click the hamburger button in the bottom left and then select “Edit Pod”
You’ll need to copy the JUPYTER_PASSWORD value (highlighted below in Green) which will be pasted into Google Colab

***NOTE***  The value for PUBLIC_KEY should match the Pub Key in the general settings that you updated in step 2.  It should auto-populate since that was done first, but if not then make sure the Pub Key value matches here which you can always paste and save.
The Docker Command should also have saved properly, but just in case you can make sure it’s in the section outlined in pink in the pic below.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/665ad7b9-972c-42e7-a8fd-3fd31d20138c/Untitled.png)
    
11. Open Google Colab.
12. Load up the WarpFusion Notebook which you will have downloaded from Sxela’s Patreon.
13. In the top right corner where it says “Connect” you’ll want to click the down arrow and choose “Connect to a Local Runtime”
14. Then for the URL you want to input this link with your JUPYTER_PASSWORD as the token (which you copied in a previous step).
[`**http://localhost:8888/?token=](http://localhost:8888/?token=)JUPYTER_PASSWORD**`
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/88a76743-a1ac-42d2-97fe-fc841ba99deb/Untitled.png)
    
15. You should now be connected to a Runpod instance with Google Colab running WarpFusion.
16. Make some cool shit!
17. Share in discord - your art, your settings, your questions, your answers, etc!