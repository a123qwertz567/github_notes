###Fedora 20 aufsetzten für Stefan

#####1. Installation
  1.1. Lankabel einstecken und Bootstick booten
  
  1.2. Installation Konfigurieren, bei der Festplattengeschichte „automatisch“ und „als Filesystem „Btrfs“
  
  1.3. .....Installation abwarten und in Fedora booten.

#####2. Standardprogramme installieren
  2.1. Github:
  
    sudo yum install git
  
  2.1. Firefox:
  
    sudo yum install firefox
  
  2.1.1 ff zum Standardbrowser machen
  
  "Systemeinstellungen" > "Standard-Komponenten" > "Webbrowser" > in die Zeile
  
    firefox
    
  eintippen
  
  2.2. easylifeproject installieren [link](http://easylifeproject.org/) und dort die passende Software auswaehlen
  
    
  2.3. Virtualbox:
  
    sudo yum install VirtualBox
    
  2.4. VLC:

    sudo yum install vlc
    
    http://mp3.ht-stream.net
    
  2.5 Steam
  
    sudo yum install steam
  
  2.6 zshel
  
    sudo yum zsh
    
  config ggf anpassen
  
  2.7 htop
  
    sudo yum install htop
  
#####3. fstab anpassen
  listet dev und UUIDS und FSTYPE
  
    lsblk -o+UUID -o+FSTYPE

  dann ggf. die fstab anpassen gemeasz den UUIDS und FSTYPE's
  
  fstab vom 30.06.2014
                                                                                                                   
    # /etc/fstab                                                                                                         
    # Created by anaconda on Sat Jun 28 16:33:09 2014                                                                    
    #                                                                                                                    
    # Accessible filesystems, by reference, are maintained under '/dev/disk'                                             
    # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info                                          
    #     
    #ssd
    UUID=b07ffb1a-b4b7-4c01-a261-2fead4da1f17 /                       btrfs   subvol=root     0 0                 
    UUID=1030e0dd-496c-42f9-a6c0-1bea391ac160 /boot                   ext4    defaults        1 2
    UUID=b07ffb1a-b4b7-4c01-a261-2fead4da1f17 /home                   btrfs   subvol=home     0 0
    UUID=e4f2a4c3-15e5-451f-9a35-bbd0ca1287a3 swap                    swap    defaults        0 0
    #500GB
    UUID=8f74da78-2bfa-4bbd-8b7d-44965ef75f44 /home/a123qwertz567/mount/500GB ext4 defaults,users   0 0
    #1500GB
    UUID=561865D21865B1A3	/home/a123qwertz567/mount/1500GB	ntfs	defaults,users	0 0
    
   Berechtigungen pruefen
   
    ls -l /home/a123qwertz567/mount/1500GB && ls -l /home/a123qwertz567/mount/500GB 

    
#####4. In Dolphin das "loeschen" aktivieren
  "Einstellungen" > "Dolphin einrichten" > "Dienste" > "Loeschen" (Checkbox aktivieren)
  
#####5. RAID1 einrichten
  2x 1TB Platzten anschliesen und NICHT mounten
  
  eine Platte sollte "btrfs" als FS haben
  
  HIER EINFUEGEN WIE MAN BTRFS MACHT
  
  dann der [Anleitung](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices#Adding_new_devices) folgen:
  
    mount /dev/sdX1 /home/a123qwertz567/mount/raid1
    btrfs device add /dev/sdX2 /home/a123qwertz567/mount/raid1
    btrfs balance start -dconvert=raid1 -mconvert=raid1 /home/a123qwertz567/mount/raid1
    
   btrfs Staus auslesen
   
      btrfs fi show
      
   RAID1 in die fstab via UUID einfuegen
   
      #RAID1
      UUID=9638bb18-4639-4617-b322-c26c6e9d2675	/home/a123qwertz567/mount/raid1		btrfs	defaults,users	0 0
    


convert -density 300 -resize 100% -quality 85 a.pdf a.png

convert dubbel_1.png dubbel_2.png dubbel_3.png dubbel_4.png dubbel_lastfaelle.pdf