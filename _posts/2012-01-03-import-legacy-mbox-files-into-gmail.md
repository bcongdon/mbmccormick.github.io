---
layout: post
title: "Import Legacy mbox Files Into Gmail"
---

One of the more notable technology problems that I encountered over the holidays last week was that of my [girlfriend](http://elizabethpuccinelli.com/)'s mom's email. She uses [Thunderbird](http://www.mozilla.org/en-US/thunderbird/) to access her email from her desktop, but recently it had been "eating" older email messages. Thunderbird had begun, with good reason, archiving her older email messages (all 75,000 of them). And somehow, this archiving process failed and she could no longer access her older messages. So we decided to move her to [Gmail](https://gmail.com) which would provide enough space for all of her email, improved spam filtering, and a much easier user interface. Gmail allowed us to import what was left in her Inbox at her old email provider via [POP3](http://en.wikipedia.org/wiki/Post_Office_Protocol) download, however some messages were still missing.

I did some research and found that Thunderbird organizes email into two separate files: an "Inbox" file and an "Inbox.msf" file. The extension-less file is actually an [mbox](http://en.wikipedia.org/wiki/Mbox) file, where all of her email is stored. The MSF file is a [Mail Summary File](http://en.wikipedia.org/wiki/Mork_(file_format)), which acts as an index to the mbox file, making it easier to access and search for individual messages. It turns out that the MSF file on the computer was corrupt, preventing us from accessing the older messages.

After some research, I found a useful utility called [IMAP Upload](http://imap-upload.sourceforge.net/) that allowed us to import these mbox files to Gmail by reading the mbox file and uploading each message to the email server using IMAP. IMAP Upload is a small [Python](http://python.org/) script and is extremely easy to use. The following command will upload email messages from the "Inbox" mbox file to Gmail and label these messages with "Imported". You will need to created this label before running this command in order for it to work properly.

{% gist 1560472 %}

The script first inspects the mbox file and then begins uploading each message to Gmail. In my case, there were 75,000 emails of varying size, so this took about 24 hours to complete. In the event that a message fails, this script will output failed messages to a separate mbox file, making it easy to restart this process if necessary. IMAP Upload worked flawlessly and Libby's mom's emails started showing up in her new Gmail account instantly.
