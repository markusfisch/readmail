Bash eMail client
=================

Probably the worlds smallest, simplest, yet full featured eMail client
without any dependencies beyond a working GNU environment running Bash.

Use it as a fallback, as a quick & slim alternative or as a tool to
read, send and manage messages.

Features
--------

Following commands are available:

	p(eek)               peek for new messages
	s(tatus)             request mailbox status
	n(ew)                list new messages only
	t(ail) [N]           list the latest N messages
	l(ist) [N[-N]]...    list messages
	r(ead) [N[-N]]...    read message
	x(tract) N[-N]...    extract attachments of message N
	f(ile) N[-N]...      file message
	d(elete) N[-N]...    remove message
	a(nswer) N           answer message
	w(rite) ADDRESS      write a message to ADDRESS
	m(ime) FILE          show a message file in MIME format (e.g. *.mbs)
	c(lear)              clear screen (or CTRL+L)
	h(elp)               show this info
	q(uit)               quit (or CTRL+D)

You may invoke the commands directly from the command line, e.g.:

	$ readmail s 'f 1' 'r 3-5' q

Or inside the interactive shell.

Configuration
-------------

Just run readmail or create a ".readmailrc" in your home directory and
put the following lines into it (fill in the values in brackets):

	POP_HOST='(your POP3 server)'
	POP_ACCOUNT='(your POP3 account)'
	POP_PASSWORD='(your POP3 password, this is optional)'

Append this block to configure your SMTP settings:

	SMTP_HOST='(your SMTP server)'
	SMTP_ACCOUNT='(your SMTP account)'
	SMTP_PASSWORD='(your SMTP password, this is optional)'

If you don't want to give passwords, readmail will ask you for it.

Examples
--------

Quickly get the size of your mailbox:

	$ readmail s q

Show your latest message:

	$ readmail r q

Get the number of new messages since the last call:

	$ FORMAT="%d\n" readmail p q

Send a message in one line:

	$ ATTACHMENTS=' ' SUBJECT='subject' BODY='body' \
		readmail 'w john@example.com doe@example.com' q

Send one or more files:

	$ ATTACHMENTS='file1 file2' SUBJECT='subject' BODY='body' \
		readmail 'w john@example.com' q
