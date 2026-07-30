## How Does Your Computer Store Things Permanently?

In the last article, you learned that RAM is a computer's working memory. RAM is extremely fast, but it only remembers information while the computer has power. Turn the computer off, and everything in RAM disappears.

Yet your documents, photos, music, apps, and operating system are still there when you turn it back on. That information has to be stored somewhere that does not depend on electricity to remember it.

That job belongs to _permanent storage_. Unlike RAM, permanent storage keeps its contents even when the computer is completely powered off. Every modern computer, phone, and tablet depends on it.

I'll explain how permanent storage works, how your computer organizes files, how it finds them when you open them, and why backups are one of the most important things you can have.


### Permanent storage vs. memory

Computers have two very different kinds of memory: RAM and permanent storage.

**RAM** is temporary working space. It holds the programs and data the CPU is using right now. It is fast, but it is also forgetful.

**Permanent storage** holds information for months or years. It stores everything that must survive a restart, including the operating system, installed applications, documents, photos and videos, downloaded files, saved games, and settings.

Think of RAM as a workbench and permanent storage as a filing cabinet.

When you open a document, the operating system copies it from permanent storage into RAM so the CPU can work with it. As you edit the document, the changes happen in RAM. When you click _Save_, the operating system writes the updated version back to permanent storage.

Without permanent storage, every computer would start from scratch every time you turned it on.

Not all storage works the same way. Modern computers use several different kinds, each with its own strengths.

### Hard disk drives (HDDs)

For many years, the hard disk drive (or _hard drive_) was the standard way to store data.

A hard drive contains one or more metal disks called _platters_ that spin thousands of times every minute. A tiny read/write head floats just above each platter and uses magnetism to store or retrieve data.

Because the platters must spin and the read/write head must move into position, hard drives are mechanical devices. That makes them slower than newer storage technologies.

Hard drives are still widely used because they offer large amounts of storage at a relatively low cost. They are common in desktop computers, external backup drives, and data centers.

Their disadvantages are equally clear:

* slower performance
* greater power consumption
* moving parts that eventually wear out
* more vulnerable to damage from drops or shocks


### Solid-state drives (SSDs)

Most new computers now use _solid-state drives_, usually called **SSDs**.

An SSD stores data in electronic memory chips. It has no moving parts.

This gives SSDs several advantages, such as much faster startup times, quicker file access, faster application loading, silent operation (no weird noises), lower power consumption, and better resistance to physical shocks.

SSDs are not perfect. They cost more per gigabyte than hard drives, although prices have fallen steadily. Their memory cells also wear out after being written many times. Modern SSDs manage this automatically by spreading writes across the drive, a technique called *wear leveling*. Under normal use, this usually allows an SSD to last for many years.


### Flash storage

The memory inside an SSD is a type of **flash memory**. The same technology is also used in USB flash drives, SD and microSD cards, smartphones, tablets, digital cameras. These devices are smaller than SSDs but work on the same basic principle: they store data electronically instead of magnetically.


### Cloud storage

Many people now save files without thinking about where they are physically stored.

Services such as **Google Drive**, **OneDrive**, **iCloud**, and **Dropbox** let you store files on computers operated by another company. Together, those remote computers are often called _the cloud_.

Cloud storage has several advantages. For example, your files can be available on multiple devices. You can share files with other people. And if your laptop is lost or stolen, your files may still be available online.

Cloud storage does _not_ replace your computer's own storage. Even when a file appears to live "in the cloud," your computer still communicates with a storage device somewhere. The difference is that the storage belongs to a remote server instead of your own computer.

Some cloud services also keep local copies of files so they can be opened without an internet connection. Others store only placeholders until you download the file. So a file may exist only on your computer, or only in the cloud, or on both at the same time.

No matter what kind of storage device you use, everything eventually becomes the same thing: **bits**.

A bit is the smallest unit of digital information. It can hold one of two values: **0** or **1**.

Your storage device does not understand photos, music, videos, or documents. It only stores enormous collections of bits.

Different kinds of files are simply different ways of arranging those bits.

A JPEG photo, a Word document, an MP3 song, and an application may look completely different to you, but to the storage device they are all sequences of binary data.

The operating system and applications know how to interpret those bits and present them as useful information.

---

### The file system

Imagine every page from every book in a library dumped into one pile, with no covers, no titles, no order. The information is still there, but finding anything would be almost impossible.

A storage device without organization would have the same problem.

The operating system needs to know what files exist, what they're named, where they live, how large they are, and who's allowed to open or change them.

The thing in your computer that keeps track of all this information is called the _file system_.

A file system is the method an operating system uses to organize and manage files on a storage device.

Without a file system, a drive would be little more than billions or trillions of numbered bytes.

A file system
- keeps track of every file and folder
- records each file's name and location
- remembers the size of every file
- stores information such as creation dates, modification dates, ownership, and permissions, and 
- keeps track of which parts of the storage device are free and which are already in use

When you save a new file, the file system finds available space and records where that file has been placed. When you open it later, the file system tells the operating system exactly where to find it.

You never have to remember where the file is physically stored. The file system does that for you.

Most operating systems have their own preferred file systems. Windows commonly uses **NTFS**. macOS uses **APFS**. Linux systems often use **ext4**, although others such as **Btrfs** and **XFS** are also common.

Many USB drives and memory cards use **exFAT**, which is supported by Windows, macOS, and Linux.

Although these file systems differ internally, they all perform the same basic job of organizing files so the operating system can store, find, update, and delete them efficiently.

Fortunately, you rarely need to know which file system your computer uses. The operating system hides almost all of the complexity. What matters is that every time you save, copy, rename, move, or delete a file, the file system updates its records so your computer can find that file again later.

### Files, folders, and paths

A file system can keep track of files only if every file has a way to be identified.

Every file has a name. The name is what you see in your file manager, such as _Vacation.jpg_, _Report.docx_, or _Budget.xlsx_. The operating system uses these names so you can recognize your files without having to remember where they are stored physically.

Most file names have two parts. The first part is the name you choose. The second part, after the final period, is called the _file extension_. It usually tells the operating system what kind of file it is.

For example, _.docx_ is a Microsoft Word document, _.jpg_ is a JPEG image, _.mp3_ is an audio file, _.pdf_ is a PDF document, and so on.

The extension does not define what a file contains. It is only a label. Renaming _photo.jpg_ to _photo.mp3_ does not turn a picture into a song. It only changes what the operating system thinks the file might be, which can prevent the correct application from opening it. 

As the number of files on a computer grows, names alone are no longer enough. Imagine trying to keep every document, photo, video, and application in a single place. Finding anything would quickly become frustrating.

To solve this problem, file systems organize files into _folders_. A folder is simply a container that holds files and other folders. This lets you group related items together and build a hierarchy, much like a filing cabinet with drawers that contain smaller folders.

For example, you might store your files like this:

```text
Documents
├── Work
│   ├── Report.docx
│   └── Budget.xlsx
├── Personal
│   └── Passport.pdf
└── Photos
    ├── Holiday
    │   └── Beach.jpg
    └── Family.jpg
```

Each folder can contain many files, many folders, or both. There is no requirement that every file have a unique name. Two files can have the same name as long as they are in different folders. For example, you could have one file named _Notes.txt_ in your **Work** folder and another named _Notes.txt_ in your **Personal** folder.

To identify a file uniquely, the operating system uses not just its name but its _path_.

A path is the complete route from the top of the file system (also called the _root_) to a particular file or folder. It tells the operating system exactly where to look.

For example, on Windows, a file might have a path like this:

```text
C:\Users\Jeremiah\Documents\Work\Report.docx
```

On macOS or Linux, the same file might look like this:

```text
/Users/jeremiah/Documents/Work/Report.docx
```

Both paths describe the same idea. Starting from the root, the operating system follows each folder in turn until it reaches the file.

You may have noticed another difference between these examples. Windows paths begin with a drive letter such as **C:**, while macOS and Linux do not.

This difference comes from how the operating systems present storage devices.

Windows assigns a _drive letter_ to each storage volume. The main storage device is usually **C:**, while additional internal drives, external drives, USB flash drives, and optical drives may appear as **D:**, **E:**, or another letter.

macOS and Linux take a different approach. Instead of assigning drive letters, they present everything as part of one continuous folder tree. Additional storage devices are attached to that tree at specific locations called **mount points**.

Both approaches achieve the same result: they allow the operating system to treat many storage devices as though they were one organized collection of files and folders.

All of this happens behind the scenes whenever you open a file.

Suppose you double-click _Report.docx_. Your file manager sends a request to the operating system, asking it to open that file.

The operating system reads the file's path one folder at a time. It starts at the root, finds the first folder in the path, then the next, and continues until it reaches the file itself.

The file system then looks up where the file's data is stored on the storage device. The data is read into RAM, where the CPU and the application can work with it. If you make changes and click **Save**, the updated data is written back to permanent storage, and the file system updates its records if necessary.

The operating system never searches the entire drive for your file. Because the file system maintains an organized record of every file and folder, it already knows where to look. Even on a drive containing millions of files, the correct file can usually be found in a fraction of a second.

This is one of the file system's most important jobs. It lets you think in terms of names and folders while it handles the much more complicated task of keeping track of where every file is stored.

---

### Ownership and permissions

Every file and folder has an owner. The owner is often the user account that created it. On a personal computer with only one user, you may never notice this. On a computer shared by several people, however, ownership helps the operating system keep each person's files separate.

Ownership works together with permissions. Permissions determine who is allowed to view, edit, or run a file.

The exact permission system varies between operating systems, but the basic idea is the same. A file or folder can allow someone or members of a group to:

* **Read** it, meaning they can open or view it.
* **Write** to it, meaning they can change or delete it.
* **Execute** it, meaning they can run it as a program.

For example, you might be allowed to open a report stored in a shared folder but not edit it. Or you might be able to view photos in a family album without being allowed to delete them.

Permissions also protect the operating system itself. Most system files are owned by special administrative accounts rather than ordinary users. This prevents applications and users from accidentally changing or deleting files that the operating system depends on.

You have probably encountered this protection when trying to rename, move, or delete a system file. Instead of carrying out the action immediately, the operating system asks you to confirm your identity or enter an administrator password. This extra step helps prevent accidental damage and makes it harder for malicious software to take control of the computer.

Modern operating systems include many other security features as well. For example, applications are often restricted to their own data unless you explicitly grant permission to access your photos, documents, camera, microphone, or location. Phones and tablets rely heavily on this kind of protection, but desktop operating systems increasingly do the same.

Some computers also _encrypt_ their storage. Encryption converts information into a form that cannot be read without the correct key. If a laptop protected with technologies such as **BitLocker** on Windows or **FileVault** on macOS is lost or stolen, encryption makes it much harder for someone else to read the files stored on the drive.

Despite these protections, storage is not perfect. Files can still be lost.

Storage devices can fail. Although hard drives and SSDs are generally reliable, they do not last forever. A hard drive may fail because its mechanical parts wear out. An SSD has no moving parts, but its memory cells can only be rewritten a finite number of times. Modern SSDs are designed to spread write operations evenly across the drive, so this limit is rarely a concern during normal use. But like any electronic device, SSDs can still fail unexpectedly.

Power failures can also cause problems. If a computer loses power while it is writing data, a file may not be saved correctly. Modern file systems reduce this risk by carefully recording changes and recovering from interruptions after the computer starts again. Serious corruption is much less common today than it was on older computers, but it can still happen.

People are often a greater source of data loss than hardware.

A file can be deleted by mistake. An important folder might be overwritten with an older version. A storage device can be formatted accidentally, erasing its contents. A laptop or phone can be lost, stolen, or damaged in a fire or flood.

Malicious software can also destroy data. One of the most damaging forms is _ransomware_. Instead of stealing your files, ransomware encrypts them and demands payment for the key needed to recover them. Even if the ransom is paid, there is no guarantee that the files will ever be restored.

For all of these reasons, no storage device should be treated as the only copy of important information.

This is why **backups** matter.

A backup is an extra copy of your data that is stored separately from the original. If the original file is lost, damaged, or deleted, you can restore it from the backup.

Many people believe that storing files in the cloud means they already have a backup. Sometimes that is true, but often it is not.

It is important to understand the difference between syncing and backing up.

A _sync service_ keeps files the same across multiple devices. If you edit a file on your laptop, the updated version is copied to your desktop, tablet, or phone. If you delete the file, the deletion may also be synchronized to every device. Syncing keeps devices consistent, but it can also spread mistakes just as quickly as it spreads useful changes.

A backup is designed for recovery, not synchronization. Good backup systems keep older versions of files and allow you to restore data even after it has been deleted or corrupted. Many cloud backup services store version history for exactly this reason.

A good rule is known as the **3-2-1 backup rule**:

* Keep **three copies** of your important data.
* Store them on **two different kinds of storage**.
* Keep **one copy somewhere else**, such as in cloud backup or at another location.

You do not need to back up every file on your computer. Programs and operating systems can usually be reinstalled. Your personal documents, photos, videos, creative work, and other irreplaceable files deserve the highest priority.

