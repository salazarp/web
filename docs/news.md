# News & events

## Harvey at FOSDEM 2016  <a name="FOSDEM 2016"></a>
January 30/31, 2016

European members of core team were at FOSDEM2016.
Changing impressions, suggestions, debating mainlines, drinking beer, meeting people...
We assisted to some devrooms and lightning talks, all of them interesting.

Here there are a couple of pictures trying to show Harvey as it was at that moment.

[![Preparing Harvey](img/fosdem2016/thumb-photo_2016-02-11_00-27-30.jpg)](img/fosdem2016/photo_2016-02-11_00-27-30.jpg)
Building and preparing the system

[![Harvey at big screen](img/fosdem2016/thumb-photo_2016-02-11_00-27-40.jpg)](img/fosdem2016/photo_2016-02-11_00-27-40.jpg)
Running Harvey! (Left to right: Keith, Sevki, Álvaro and Rafael)

---
## Things you can do now in Harvey <a name="Factotum, Fossil disk, Go and drawterming Harvey"></a>
December 20, 2015

Many new things have been changed or implemented last months. We were working a lot and now, even for our own eyes, we went far away than we thought at the begining, almost a year ago. But we want more, so remember: we need programmers. Are you ready to join Harvey?

Harvey has now an almost stable kernel:

>What means you can start to do programs and experiments in it.

We are able to use [drawterm](https://github.com/0intro/drawterm) with Harvey:

>Don't forget to try mclock, courtesy of John DeGood.

Factotum is working:

>Well, if you don't know what it means, you should to read [some lines](http://plan9.bell-labs.com/plan9/factotum.html) about it first.

System console are now splitted in three types:

>And all of them out of kernel in user space, thanks to Giacomo Tesio. Just check the code to see how they work and the purpose of everyone.

Now we are able to play with Go programming language:

>There are some limitations, This is a work in progress. Never quite graceful to Ron Minnich for this and many other things.

Harvey has now Fossil and Venti:

>So you can set up a disk (real and virtual) for your system installation. Check our wiki to see how to do it. Courtesy of Rafael Fernández, who fought hard with Fossil.

And don't forget you can come to meet us in [Fosdem 2016](http://fosdem.org), you will recognize us for our Harvey T-Shirts. Do you want one of them? check [here](http://www.zazzle.com/harvey_os_supplies).

---

## Using gdb to debug Harvey <a name="debugging-harvey-gdb"></a>
August 8, 2015

A page has been added to the wiki which describes how to debug Harvey using gdb.  See [Debugging Harvey in gdb](https://github.com/Harvey-OS/harvey/wiki/Debugging-Harvey-in-gdb) for details.

---

## APE is ready <a name="ape-is-ready"></a>
August 6, 2015

APE (the [ANSI/POSIX Environment](http://plan9.bell-labs.com/sys/doc/ape.html)) has been finally given the green light:

>ANSI people, it's your time. Let's go, doors are opened. Ape is working.
>Improvements, suggestions are welcome. Ports can be done. Wiki is ready in github.

This means a whole host of ports can be on their way fueled by POSIX -sort of- compliance:

>  There are some aspects of required POSIX behavior that are impossible or very hard to simulate in Plan 9.
>  Experience has shown, however, that the simulation is adequate for the vast majority of programs.

A quick [getting started with APE](https://github.com/Harvey-OS/ape/wiki/Getting-Started) guide is being drafted in the wiki.

---

## Broken scheduler, working scheduler<a name="broken-scheduler"></a>
August 1, 2015  

Despite the hot summer, Harvey has been progressing steadily during these months. So, a big THANK YOU to everyone involved, you all rock!

Obviously, it can't all be happy days: resident guru Aki Nyrhinen has just proved how things can easily fall into chaos by detecting a major defect in Harvey's core. Straight from the horse's mouth:

>it turns out that the scheduler in harvey is badly broken.
>it does not do time sharing at all, among other things.
>it also crashes instantly if squidboy is enabled (>1 core).
>the procs aren't really reusable at all, because the kernel structures are apparently infested with pointers to the procs when one does an exit.
>there's a lot to be fixed here.

Undeterred by the mess, and in a question of hours, the fire has been put out:

>Alright, after 4 hours of furious editing and undoing damage to the boot code, I've got harvey booting up with the ndnr() in squidboy commented out.

Some (thorough?) measurements after the fix:

>Boot faster.
>CPU at 13% as usual (we still have pending a new random).
>No weird behaviours.
>Nice job!

Hooray!

---

## USENIX presentation slides available <a name="usenix-2015-materials"></a>
July 20, 2015

Here are Harvey's [presentation slides](docs/Harvey-Usenix-2015-ATC-BOF-slides.pdf) at USENIX 2015 ATC BOF.

We will update this note when we can link to a video of the talk.

---

## Looking for developers! <a name="developers-wanted"></a>
July 15, 2015

For the next couple of months, the project is looking for developers to step up and help get Harvey ready for prime time.

> "I think the big goal for the next two months, the single most important goal, is to move a needle: we want more people contributing"

There still exist areas for continued development, and YOU can make a difference. This experience can make for an ideal project for Operating System courses and the like. Please talk to us!

> "For new people: we have troubles with sdiahci.c, ahci driver. So we haven't local disk for now. It's not blocking at all, but other improvements depends on it. But, what would you like to do with Harvey meanwhile?"

---

##Harvey at USENIX 2015 <a name="usenix-2015"></a>
July 8, 2015


It's usenix and we have a BOF tomorrow night, so we have to get the
minicluster going. Five AMD Persimmon boards in a stack and 1 Minnow
MAX.

We had really high hopes for the minnow max but it is a bit of a
disappointment. Super neat size -- see the little blue box hanging
from an ethernet cable in the 5th picture? It was kind of exciting to
see so much in such a small box.

We've concluded that to make this board usable for Harvey we're going
to need to swap out UEFI for some other firmware. it took us 15
minutes just to walk through enough of the commands and dialogues to
realize we can only boot from a FAT-formatted SD card. FAT
formatted. 2015. What's wrong with this picture?

So then tried PXE boot. See John taking a movie of the TV? It's
because when UEFI pxeboot fails, it puts the failure frame up for 1/30
second and clears it. So John took a movie, and then we watched the
movie frame by frame to see the error. 

Then we hit the next problem: once we
got the special version of GRUB booting over the LAN, it told
us we wouldn't have a visible console. We need a console.

The AMD stack, with three coreboot nodes and two AMI BIOS nodes,
worked better. The only thing that went wrong is that the AMI BIOS
breaks pxelinux.0 -- it loads and gets to some point, and then instant
reset. We can still boot harvey on the AMI BIOS nodes, but only from a USB stick. 
We'll be reflashing these too. 

[![mini cluster](img/usenix2015/thumb-mini-cluster.jpg)](img/usenix2015/mini-cluster.jpg)
Harvey mini-cluster ready to fire up (or catch fire)

[![boffins to blame](img/usenix2015/thumb-boffins-to-blame.jpg)](img/usenix2015/boffins-to-blame.jpg)
John on the floor, trying to make the minnowmax boot
Harvey, Aki on the chair making Harvey build on a mac and boot off of one.

[![video of error](img/usenix2015/thumb-video-of-error.jpg)](img/usenix2015/video-of-error.jpg)
John decided taking a video of the boot sequence would
be the best way to capture the sub-second error message.
