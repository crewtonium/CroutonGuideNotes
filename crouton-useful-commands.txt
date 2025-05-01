📂 /
├── 💻 VT2 (Ctrl+Alt+F2)
│   └── 👤 Login as chronos/root
│       └── 💾 /media/removable/USBDRIVE
│           ├── 📁 crouton
│           │   ├── 🗂️ chroots
│           │   │   └── 🐧 bullseye
│           │   │       ├── 📄 rootfs
│           │   │       └── 📄 other-chroot-files
│           │   └── ⚙️ enter-chroot
│           └── 🛠️ (optional: remount exec)
│
└── 📝 Commands
    ├── cd /media/removable/USBDRIVE/crouton/chroots/bullseye
    ├── sudo mount -o remount,exec /media/removable/USBDRIVE
    └── sudo sh /media/removable/USBDRIVE/crouton/enter-chroot -c /media/removable/USBDRIVE/crouton/chroots/bullseye

1️⃣ Upgrading Packages in the Chroot (CLI Only)
text
📂 /
└── 🐧 Inside chroot (after enter-chroot)
    ├── 🔄 Update package lists
    │   └── sudo apt update
    ├── ⬆️ Upgrade all packages
    │   └── sudo apt upgrade
    ├── 🧹 Remove unused packages
    │   └── sudo apt autoremove
    └── 📝 Full upgrade (optional)
        └── sudo apt full-upgrade

2️⃣ Copying Files Between ChromeOS and Chroot
text
📂 /
├── 💻 ChromeOS shell (VT2)
│   ├── 📁 /home/chronos/user/Downloads
│   └── 📁 /media/removable/USBDRIVE/crouton/chroots/bullseye/home/<youruser>
│
└── 📝 Commands
    ├── 📤 Copy from ChromeOS to chroot:
    │   └── sudo cp /home/chronos/user/Downloads/file.txt /media/removable/USBDRIVE/crouton/chroots/bullseye/home/<youruser>/
    └── 📥 Copy from chroot to ChromeOS:
        └── sudo cp /media/removable/USBDRIVE/crouton/chroots/bullseye/home/<youruser>/file.txt /home/chronos/user/Downloads/

3️⃣ Adding a New User to Your Chroot
text
📂 /
└── 🐧 Inside chroot (after enter-chroot)
    ├── 👤 Add new user
    │   └── sudo adduser newusername
    ├── 🔑 Set password
    │   └── sudo passwd newusername
    └── 🧑‍🤝‍🧑 Add to sudo group (optional)
        └── sudo usermod -aG sudo newusername

4️⃣ Backing Up Your Chroot to Another USB or Location
text
📂 /
├── 💻 ChromeOS shell (VT2)
│   ├── 💾 /media/removable/USBDRIVE/crouton/chroots/bullseye
│   └── 💾 /media/removable/BACKUPDRIVE/
│
└── 📝 Commands
    ├── 🗜️ Create compressed backup:
    │   └── sudo tar czvf /media/removable/BACKUPDRIVE/bullseye-backup.tar.gz -C /media/removable/USBDRIVE/crouton/chroots bullseye
    └── 📦 Extract backup (restore):
        └── sudo tar xzvf /media/removable/BACKUPDRIVE/bullseye-backup.tar.gz -C /media/removable/USBDRIVE/crouton/chroots
