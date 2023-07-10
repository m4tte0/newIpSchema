
A New IPs Schema Proposal
=========================

**Author**: mathon < mhonfucci (at) sica-italy (dot) com >

**Status**: Draft

**Type**: Process

**Created**: 09-Jun-2023


Abstract
--------

**Forward**: the present file aims to highlight a common rule to yield all the
available IPs needed to configure the whole set of PLCs a multiline project is
consisting of.


The IPs Rule
------------

Given the current standard machine reference number, i.e.:

		c/yy.nnnn/0L/0M/01/01

and the choice to keep using _linklocal_ addresses to address all its fieldbus
devices, that is from the block **169.254.0.0/16** - which can be expanded as
follows:

		from: 169.254.0.1
		  to: 169.254.255.255

we shall preserve the last octet, which refers to the *machine backbone* (each).

Along with this constraint and the aim exposed above in mind, we need to find a
rule capable of coding */0L* and */0M* info inside the third octet (only).

Since it's reasonable enough not to consider more than 20 machines per line, it
thus comes natural to slipt the range spanning from address 169.254.1.1/16 to
169.254.253.253/16 into **blocks of 20 IPs each**.

Now let's focus on the third octet only: the *largest integer* multiple of 20
but lower than 253 is **240**, yielding *12 comeplete lines* of machines which
can be mapped fully with the scheme below:

		169.254.<20(L-1) + M>.0/24


Use Cases
^^^^^^^^^

So, for instance, *all machines* of the first line - /01/0M - would then be
assigned to the following block of addresses:

	- 169.254.  1.0/24	:: /01/01
	- 169.254.  2.0/24	:: /01/02
	- 169.254.  3.0/24	:: /01/03
	- 			..
	- 169.254. 20.0/24	:: /01/20

and so on for the second one - that is /02/0M:

	- 169.254. 21.0/24	:: /02/01
	- 169.254. 22.0/24	:: /02/02
	- 169.254. 23.0/24	:: /02/03
	- 			..
	- 169.254. 40.0/24	:: /02/20

One would immediately sees that for all the other 10 lines it holds the 
following:
	
	- 169.254. 41.0/24	:: /03/01
	- 169.254. 61.0/24	:: /04/01
	- 169.254. 81.0/24	:: /05/01
	- 169.254.101.0/24	:: /06/01
	- 169.254.121.0/24	:: /07/01
	- 169.254.141.0/24	:: /08/01
	- 169.254.161.0/24	:: /09/01
	- 169.254.181.0/24	:: /10/01
	- 169.254.201.0/24	:: /11/01
	
	- 169.254.221.0/24	:: /12/01
	- 169.254.222.0/24	:: /12/02
	- 169.254.223.0/24	:: /12/03
	- 			..
	- 169.254.240.0/24	:: /12/20


With this scheme it also turns out that some blocks might be resereved as
follows:

	- 169.254.  0.0/24	:: RESERVED > NOT TO BE USED
	
	- 169.254.241.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.242.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.243.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.244.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.245.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.246.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.247.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.248.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	- 169.254.249.0/24	:: AVAILABLE > OTHER MACHINES (not SICA)
	
	- 169.254.250.0/24	:: AVAILABLE > NETWORKING TASKS AND NEEDS
	- 169.254.251.0/24	:: AVAILABLE > NETWORKING TASKS AND NEEDS
	- 169.254.252.0/24	:: AVAILABLE > NETWORKING TASKS AND NEEDS
	- 169.254.252.0/24	:: AVAILABLE > NETWORKING TASKS AND NEEDS
	
	- 169.254.253.0/24	:: RESERVED > NOT TO BE USED
	- 169.254.254.0/24	:: RESERVED > NOT TO BE USED
	- 169.254.255.0/24	:: RESERVED > NOT TO BE USED
