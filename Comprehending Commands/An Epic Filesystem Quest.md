# Comprehending Commands

## An Epic Filesystem Quest
With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:
```
hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
```
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!
Good luck!



### Solve
**Flag:** `pwn.college{4xhA86kAvoEtVduzII7JKVY5ddo.QX5IDO0wSNyMzNzEzW}`

The first clue is located in the root directory. Listing the files in root directory using `ls` shows a file named `MEMO`. Reading the file using `cat` gives us the path to the directory in which the next clue is located.

Listing the files in the next directory shows a file named `EVIDENCE`. Reading the file gives us the path to the directory in which the next clue is located.

Similarly, listing the files in the next directory shows a file named `DISPATCH`. Reading the file gives us the path to the directory in which the next clue is located. However, this time we are not allowed to change our current working directory.

We can list the files in the next directory using its absolute path, eliminating the need to change our working directory. Doing so shows a file named `WHISPER-TRAPPED`. Reading the file gives us the path to the directory in which the next clue is located. However, as last time, we are not allowed to change our current working directory.

Again, we can list the files in the next directory using its absolute path. Doing so shows a file named `NOTE-TRAPPED`. Reading the file gives us the path to the directory in which the next clue is located. This time, we are told to specifically look for the clue by changing our working directory.

Using `cd` to change our working directory, we can list the files in it. Listing the files in the next directory shows a file named `NUGGET`. Reading the file gives us the path to the directory in which the next clue is located. Again, we are told to specifically look for the clue by changing our working directory.

Using `cd` to change our working directory, we can list the files in it. Listing the files in the next directory shows a file named `CUE`. Reading the file gives us the path to the directory in which the next clue is located. However, we are told that the next file-name is dot prepended.

To list all files, *including* dot-prepended ones, we can use `ls` with the flag `-a`. Doing so shows a file named `.CLUE`. Reading the file gives us the path to the directory in which the next clue is located.

Listing the files in the next directory shows a file named `DOSSIER`. Reading the file gives us the required flag.
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  MEMO        boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ cat MEMO
Yahaha, you found me!
The next clue is in: /usr/local/lib/python3.8/dist-packages/angr/simos
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/local/lib/python3.8/dist-packages/angr/simos
EVIDENCE  __init__.py  __pycache__  cgc.py  javavm.py  linux.py  simos.py  snimmuc_nxp.py  userland.py  windows.py
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/local/lib/python3.8/dist-packages/angr/simos/EVIDENCE
Great sleuthing!
The next clue is in: /usr/share/racket/pkgs/srfi-lite-lib/srfi/29
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/racket/pkgs/srfi-lite-lib/srfi/29
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ ls
DISPATCH  bundles  compiled  localization.rkt
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ cat DISPATCH
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/numpy/f2py/tests/src

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ ls /usr/local/lib/python3.8/dist-packages/numpy/f2py/tests/src
WHISPER-TRAPPED     assumed_shape    cli           f2cmap  module_data      quoted_character  return_complex  return_real  value_attrspec
abstract_interface  block_docstring  common        kind    negative_bounds  regression        return_integer  size
array_from_pyobj    callback         crackfortran  mixed   parameter        return_character  return_logical  string
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ cat /usr/local/lib/python3.8/dist-packages/numpy/f2py/tests/src/WHISPER-TRAPPED
Congratulations, you found the clue!
The next clue is in: /opt/pwndbg/docs/commands/xor

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ ls /opt/pwndbg/docs/commands/xor
NOTE-TRAPPED  memfrob.md  xor.md
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ cat /opt/pwndbg/docs/commands/xor/NOTE-TRAPPED
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/tools/perf/arch/sh/util

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/29$ cd /opt/linux/linux-5.4/tools/perf/arch/sh/util
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/arch/sh/util$ ls
Build  NUGGET  dwarf-regs.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/arch/sh/util$ cat NUGGET
Yahaha, you found me!
The next clue is in: /usr/include/linux/netfilter

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/tools/perf/arch/sh/util$ cd /usr/include/linux/netfilter
hacker@commands~an-epic-filesystem-quest:/usr/include/linux/netfilter$ ls
CUE                          nfnetlink_acct.h       xt_CONNSECMARK.h  xt_TCPMSS.h       xt_conntrack.h  xt_length.h     xt_realm.h
ipset                        nfnetlink_compat.h     xt_CT.h           xt_TCPOPTSTRIP.h  xt_cpu.h        xt_limit.h      xt_recent.h
nf_conntrack_common.h        nfnetlink_conntrack.h  xt_DSCP.h         xt_TEE.h          xt_dccp.h       xt_mac.h        xt_rpfilter.h
nf_conntrack_ftp.h           nfnetlink_cthelper.h   xt_HMARK.h        xt_TPROXY.h       xt_devgroup.h   xt_mark.h       xt_sctp.h
nf_conntrack_sctp.h          nfnetlink_cttimeout.h  xt_IDLETIMER.h    xt_addrtype.h     xt_dscp.h       xt_multiport.h  xt_set.h
nf_conntrack_tcp.h           nfnetlink_log.h        xt_LED.h          xt_bpf.h          xt_ecn.h        xt_nfacct.h     xt_socket.h
nf_conntrack_tuple_common.h  nfnetlink_osf.h        xt_LOG.h          xt_cgroup.h       xt_esp.h        xt_osf.h        xt_state.h
nf_log.h                     nfnetlink_queue.h      xt_MARK.h         xt_cluster.h      xt_hashlimit.h  xt_owner.h      xt_statistic.h
nf_nat.h                     x_tables.h             xt_NFLOG.h        xt_comment.h      xt_helper.h     xt_physdev.h    xt_string.h
nf_synproxy.h                xt_AUDIT.h             xt_NFQUEUE.h      xt_connbytes.h    xt_ipcomp.h     xt_pkttype.h    xt_tcpmss.h
nf_tables.h                  xt_CHECKSUM.h          xt_RATEEST.h      xt_connlabel.h    xt_iprange.h    xt_policy.h     xt_tcpudp.h
nf_tables_compat.h           xt_CLASSIFY.h          xt_SECMARK.h      xt_connlimit.h    xt_ipvs.h       xt_quota.h      xt_time.h
nfnetlink.h                  xt_CONNMARK.h          xt_SYNPROXY.h     xt_connmark.h     xt_l2tp.h       xt_rateest.h    xt_u32.h
hacker@commands~an-epic-filesystem-quest:/usr/include/linux/netfilter$ cat CUE
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/sage/algebras/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/include/linux/netfilter$ cd /usr/lib/python3/dist-packages/sage/algebras/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/algebras/__pycache__$ ls -a
.                                         commutative_dga.cpython-38.pyc                q_system.cpython-38.pyc
..                                        free_algebra.cpython-38.pyc                   quantum_matrix_coordinate_algebra.cpython-38.pyc
.CLUE                                     free_algebra_element.cpython-38.pyc           quaternion_algebra.cpython-38.pyc
__init__.cpython-38.pyc                   free_algebra_quotient.cpython-38.pyc          quaternion_algebra_element.cpython-38.pyc
affine_nil_temperley_lieb.cpython-38.pyc  free_algebra_quotient_element.cpython-38.pyc  rational_cherednik_algebra.cpython-38.pyc
algebra.cpython-38.pyc                    free_zinbiel_algebra.cpython-38.pyc           schur_algebra.cpython-38.pyc
all.cpython-38.pyc                        group_algebra.cpython-38.pyc                  shuffle_algebra.cpython-38.pyc
askey_wilson.cpython-38.pyc               hall_algebra.cpython-38.pyc                   tensor_algebra.cpython-38.pyc
associated_graded.cpython-38.pyc          iwahori_hecke_algebra.cpython-38.pyc          weyl_algebra.cpython-38.pyc
catalog.cpython-38.pyc                    jordan_algebra.cpython-38.pyc                 yangian.cpython-38.pyc
cellular_basis.cpython-38.pyc             nil_coxeter_algebra.cpython-38.pyc            yokonuma_hecke_algebra.cpython-38.pyc
clifford_algebra.cpython-38.pyc           orlik_solomon.cpython-38.pyc
cluster_algebra.cpython-38.pyc            orlik_terao.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/algebras/__pycache__$ cat .CLUE
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/arch/parisc/oprofile
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/algebras/__pycache__$ cd /opt/linux/linux-5.4/arch/parisc/oprofile
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/parisc/oprofile$ ls
DOSSIER  Makefile  init.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/parisc/oprofile$ cat DOSSIER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{4xhA86kAvoEtVduzII7JKVY5ddo.QX5IDO0wSNyMzNzEzW}
```

### New Learnings

This challenge combines all previously learnt concepts and commands in one single challenge.

