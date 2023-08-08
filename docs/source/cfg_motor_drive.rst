===========================================
kb131.17 - Commutation Angle for BLDC Motor
===========================================

| **Author**: mathon <mhonfucci (at) sica-italy (dot) com>
| **Status**: Draft
| **Type**: ServoDrive
| **Created**: 13-Jul-2023

Abstract
========

This KB aims to collect, drive by drive, the *commutation angle* for each and
every BLDC motor used in the current production of machineries — as of July 13th
2023.

By creating a database of such a values, will let the drive parametrization to
be faster and more efficient - since not knowing this parameter' value would
inevitably led to perform a *rotative autotuning* of the motor itself, with the
resulting need to have its shaft not geared given that it will shall spinning
free.


The Database
============

**Last Update**: 13-Jul-2023

+--------------------+----------------------------------------------------+--------------------------------------------------+
| MACH REF NUM       | MOTOR                                              | DRIVE                                            |
+                    +-------------------------+--------------------------+----------------+-------------------+-------------+
|                    | code                    | ratings                  | KEB F5 - EC.02 | KEB S6/F6 - EC.23 | NIDEC 3.025 |
+====================+=========================+==========================+================+===================+=============+
| eBell3 | New eBell | BR0782044 WG 1300C001   | 26 Nm – 5.445kW – 11.1 A | < ? >          | 43454             | < ? >       |
+--------------------+-------------------------+--------------------------+----------------+-------------------+-------------+
| eBell3             | BR0762042 WG 1300C001   | 19.5Nm – 4.08 kW – 8.54A | < ? >          | 43466             | < ? >       |
+--------------------+-------------------------+--------------------------+----------------+-------------------+-------------+
| Flash 450          | BR0363040 I1 MBK 500003 |  1.9Nm – 0.597kW – 1.37A | < ? >          | 11045             | < ? >       |
+--------------------+-------------------------+--------------------------+----------------+-------------------+-------------+
| Flash 450          | BR0343040 I1 MBK 500003 |  1.3Nm – 0.408kW – 0.91A | < ? >          | 10734             | < ? >       |
+--------------------+-------------------------+--------------------------+----------------+-------------------+-------------+
| Flash 450          | BR0823042 WH 13DDI001   | 32 Nm – 8.482kW – 17.2 A | < ? >          | 57057             | < ? >       |
+--------------------+-------------------------+--------------------------+----------------+-------------------+-------------+
