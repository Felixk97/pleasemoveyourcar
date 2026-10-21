CAR CONTACT QR - DIRECT TO WHATSAPP (USERNAME)
==============================================

What it does
------------
Anyone who scans the QR code on the car is sent straight to a WhatsApp
chat with the owner's WhatsApp username. The owner's phone number is not
shown. A message is already filled in, e.g.:
  "Hi, I am contacting you about your vehicle QAB36D."

Live link (same as the QR code): https://pleasemoveyourcar.netlify.app/

Files
-----
public/index.html   The page. Redirects the visitor to WhatsApp.
netlify.toml        Tells Netlify the site files are in the "public" folder.
README.txt          This file.

IMPORTANT: index.html must stay inside the "public" folder in GitHub.
If it is at the top level, Netlify fails with
"Deploy directory 'public' does not exist".

Settings you can change (top of the script in public/index.html)
-----------------------------------------------------------------
WA_USERNAME      Your WhatsApp username, without the @.
                 Currently: nicolebabooo
VEHICLE_PLATE    The plate shown and used in the message.
                 Currently: QAB36D
                 (Find:  params.get('plate') || 'QAB36D'  and change QAB36D)
Message text     Find the line starting:  const text = 'Hi, I am contacting you...
                 and edit the wording.

How to update the site
----------------------
1. Open your repo on GitHub: Felixk97/pleasemoveyourcar
2. Open public/index.html and click the pencil (edit) icon.
3. Make the change and click "Commit changes".
4. Netlify redeploys automatically (check the Deploys tab for "Published").
The QR code does not change.

First-time setup
----------------
1. Upload the "public" folder and netlify.toml to the TOP LEVEL of your
   GitHub repo (drag the public folder itself, not just the files inside).
2. In Netlify: Add new site > Import an existing project > pick the repo.
   No build settings are needed.
3. Open the live link on a phone that is NOT yours and check that WhatsApp
   opens a chat with your username.

Files you no longer need
------------------------
From the earlier ntfy version you can delete these from the repo if you
want it tidy (they do nothing now):
  visitor.html, reply.html, owner-setup.html, send-alert.js, package.json
The NTFY_TOPIC environment variable in Netlify is also no longer used.

Notes
-----
- The visitor's own phone number is visible to you in the WhatsApp chat.
- WhatsApp username chat is still rolling out. If a visitor's WhatsApp
  does not support it yet, the link may not open a chat for them.
- Some in-app QR scanners block automatic redirects. The page has an
  "Open WhatsApp" button for that case.
