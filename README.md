

Installation guide step by step:

 1. Download Termux
   Open browser to github.com/termux/termux-app/releases and download the latest universal or arm64 apk.
 
2. Install app
   Install the downloaded file (Click install anyway if play protect warning appears)
 
3. Storage permission
   Open Termux, run this command, and tap allow on your phone popup.
   termux-setup-storage
 
4. Update system
   Get the latest packages and press Enter on your keyboard if it pauses to ask a Y/I/N/O/D/Z question.
   pkg update && pkg upgrade -y

 5. Install tools
   Install the packages we need for downloading and fixing the network.
   pkg install wget tar proot resolv-conf -y

 6. Download server
   Get the filebrowser server file.
   wget https://github.com/filebrowser/filebrowser/releases/latest/download/linux-arm64-filebrowser.tar.gz
 
7. Extract server
   Unpack the filebrowser file.
   tar -xvf linux-arm64-filebrowser.tar.gz

 8. Download tunnel
   Get the ngrok file.
   wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-arm64.tgz

 9. Extract tunnel
   Unpack the ngrok file.
   tar -xvf ngrok-v3-stable-linux-arm64.tgz

 10. Add token
   Replace PCH_TOKEN with your real ngrok token.
   ./ngrok config add-authtoken PCH_TOKEN

 11. Start internal server
   Run this to start the server for internal storage and write down the random admin password it prints out.
   ./filebrowser -a 127.0.0.1 -p 8080 -r ~/storage/shared

 12. New tab
   Swipe from the left edge of the screen inside Termux and tap New session.

 13. Fix network
   Run this in the new tab so the tunnel can bypass the phone network restrictions.
   termux-chroot

 14. Start tunnel
   Run this to generate your global web link.
   ./ngrok http 8080

 15. Open web link
   Open a browser on any device, go to the ngrok link, and click Visit Site.
 
16. Log in
   Use the username admin and the random password you wrote down in step 11 to see your internal files.
 
17. SD card setup (optional)
   Go back to your first Termux tab, press CTRL on the Termux keyboard, then press c to stop the server.

 18. SD card folder (optinal)
   Open your phone file manager, go to your SD card, and make this exact folder path for uploads.
   Android/data/com.termux/files

 19. Refresh storage (optional)
   Run this in the first Termux tab so it detects the new SD card folder.
   termux-setup-storage

 20. Restart with SD card (optinal)
   Run this to start the server again with access to all drives and the SD card fix.
   ./filebrowser -a 127.0.0.1 -p 8080 -r ~/storage --followExternalSymlinks

 21. Show both drives (optional)
   Refresh the browser page, and it will now show internal and external folders.

 22. Change password
   In the web interface, click Settings, go to Profile, and change the password.

 23. Disable battery optimization
   Go to phone settings, apps, select Termux, go to battery, and set it to Unrestricted.

 24. Keep background alive
   Pull down your phone notification bar, find the Termux notification, and tap Acquire wakelock.

 25. Server hardware care
   Plug the phone into a charger (5w recomended) and always keep the wifi/mobile data on.
