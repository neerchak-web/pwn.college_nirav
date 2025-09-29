# Processes and Jobs

## Killing Misbehaving Processes 
Sometimes, misbehaving processes can interfere with your work. These processes might need to be killed...

In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which (like in the Practicing Piping FIFO challenge) /challenge/run wants to write your flag. You need to kill this process.

Your general workflow should be:

Check what processes are running.
Find /challenge/decoy in the list and figure out its process ID.
kill it.
Run /challenge/run to get the flag without being overwhelmed by decoys (you don't need to redirect its output; it'll write to the FIFO on its own).
Good luck!

NOTE: You might see a few decoy flags show up even after killing the decoy process. This happens because Linux pipes are buffered: conceptually, they have a sort of length through which data flows, and you might kill the decoy process while data is in the pipe. That data, having already entered the pipe, will proceed to the other end (your cat). If you wait a second, you'll see the decoys stop, and then you can /challenge/run and win!



### Solve
**Flag:** `pwn.college{sdMlJQw8-_jzaBkPzIoiKT9XFJC.0FNzMDOxwSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`. Doing so will write the flag into the FIFO file `/tmp/flag_fifo`. However, another program `/challenge/decoy` has opened the FIFO file in write mode.

To terminate `challenge/decoy`, we can find its process id using `ps -ef` and use the `kill` command. After doing so, running `/challenge/run` will open the FIFO file in write mode.

For the data to actually get written into the file, we need to start reading it from another terminal window using `cat`. Doing so will display lines of false flags which were in the pipe when `/challenge/decoy`. However, the last line is the required flag, as the last line was written into the file by `/challenge/run`.

```
ps -ef | grep /challenge/decoy
root         139       1  0 15:25 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       142     139  0 15:25 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       362     352  0 15:27 pts/0    00:00:00 grep --color=auto /challenge/decoy
kill 142
/challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{z7vZ0tlRJKRkLv0KnU1oz50Xw5nuNnGFcB1xgtuc32cTXKZ}
pwn.college{Xbn3Y4WmXD.ZYeZ.uFTX7oFT9Ze5SuZfQtPcmh3kbqiMWSx}
pwn.college{OKHfSuOgKFVFRJoa24CY44PYN8SU4StFl9vDtu9Wjb.XoYm}
pwn.college{tYHTBw255.RHZ6yxlKT6AeQ3tM06IOfYnzsy0FoDsMdrbvm}
pwn.college{0u4klaFdEMt2kTf7Mm7J0Ix3kg6zDrc0U67MGau48tgFWZJ}
pwn.college{aK1527ZAiPdcBny.3PTy.bEO0r-xKsu49x30WUzZH5xoFdJ}
pwn.college{MoYvWlr.6JtEIjCXg296dcUbccU.JGjum6FnrhS-nvF3wAK}
pwn.college{lCA4eNJMiAeJptSAHsLs1SBKhCODuY1fgOvfX5PSRihmbSN}
pwn.college{FvllkXQbKKQUYSPkkb1PIzdppwbDGUYm.NaU-fTXcSBqgnq}
pwn.college{cg5bAqBCj3KuqdtVHnQ1JK66RqMkA62eCvCljWG2sN4qfjb}
pwn.college{vxLnbQB-ZB.BAfqq6CKsB5IRpfjM1Kcu3I05BAj62h096KC}
pwn.college{4PY3no0O6sHl6g55LpbduLXNagb7XdHYNd3EKODsLTDI5QI}
pwn.college{LSFZw2gVISIHXUcxUD3CCd2pcSfebMdCR.9Pyo62nFchSvG}
pwn.college{clwWAF.1xG2q6kWfdZgV9UJWHNUOBbgwqJbCzQZm1ZAFmQy}
pwn.college{lfOyRMpOqHT-LZ4uZB1GYaj2BLwP4CSmE3u5nUH.TJtVxWg}
pwn.college{OiJ0ZDitsEaNFXmrKojVxuKmaoYPOgaQYdY4HHy1eUBod9I}
pwn.college{MS5-R7drRVNUGJ2Pcx9CItSlRbjATCr7rcmJ9Qp9BXZIIrz}
pwn.college{J9.I7knKtcRYlThmT2kCrS1wZe8tPuSIP7SYwmM.K7DL4Mr}
pwn.college{zsnvEQIhQjqheGKwdCJJkqSSuV6hfNRE8mXV1P6n2P4s1g4}
pwn.college{8MrBVQw0S9XRIr0YRQvAzK3ZtWmS5XHT-VxYPQ8udlXZI8m}
pwn.college{SWMmEkUhXNunwr41lFeEt6xIujEuIPY7gg5tBJCYD6gY-mp}
pwn.college{B66nealUM-KlSyH0GvnPwLmWzp2hx9caCRggh.o0txENElw}
pwn.college{aC2-3OuouvCDeiCX8PcYodZaV7XLHh3MOB3cicq44ni1HtF}
pwn.college{n8R-.ECw1aKztHqcL9gMdMJ7Vybo8fXkorD9qfZFOnwBX8x}
pwn.college{F3cuGCIQvtjmoRiPf125JeGKekGcOk-630SgIr8IWEJpbwD}
pwn.college{caGuLrqZwbf56AyTrgsAdxPRTZ-zABALvzC70PxkDEm46Uu}
pwn.college{GLR1y3hSTCCbPARySKXh6lxfqR2zIt6NRCbigaX1zhNsOOq}
pwn.college{Zc49jvL8KjTwDkXrOPWHbcIJL6qA1wBIpVRsAyXwaiZ6FIe}
pwn.college{qSMzgE4KtmMbbIyfc.3WGVhMLh2RdfVubXLcW6hV7C74d50}
pwn.college{hmWbotJ08bnFdam8pp3B9V.9l68au3q.gFACc63Lh4h1emm}
pwn.college{TfNYdMs4GjrWk7WE8vaTdYcAOXGfsM4YO1cAlhW6Z9xX7tP}
pwn.college{6aZuNAIF76G.yo4BN5nnpJyxdx9fSQXCSUZdOl0aGWs.ILF}
pwn.college{gMdWQCGwmUqmKoTJgQ2kNHKuIxvxeStZsWkNL1zMZ19qzR6}
pwn.college{ep0vMXrA-W2t3Ei0LnwR2ctbtfXm3ftNX2cdKhOBI9JiFuN}
pwn.college{ACQukYAVZJtRhWtIUB-UyQUmuRIMFqL35yj8fwP1FS4vOxf}
pwn.college{bJVjkYOslwFKs8ec8hB0rYiTlw9DotazSKN9vKzujLTOceW}
pwn.college{fWcSVDuemuH2g6MwH5bkRpAaaxq-N4kZEsyMRIZsvMhT0YT}
pwn.college{zeV-dVXaj-MDIirlQuM-tui01dBREyuh9vQnk4Dxd21OwCv}
pwn.college{IXSNpOd2kvPMGjkfKuh-4.fIp7KM8CugENVGpPPlSQNRJZJ}
pwn.college{ez.5ecaDga6-.RbXBgLI4xStk4spwUIe5IJpinHn0xKXX1t}
pwn.college{1lXAL-2sa8wMWNpZXFb4RTeqxlAbwqwKaCeAP3qw78BzE3U}
pwn.college{KKcb0rFZEEURYy2zR2nHjwaJkPmZYFpE264YWLbiMdyAQ15}
pwn.college{l-JvwQZOX65SzCzoys9FG-Z5t9fOpc7BgbclNkuU6BKV4WI}
pwn.college{6EAOgl5lJF0eZQ10I.PjLBWWxm4QJm75wLqCboDD0Ek9Ufd}
pwn.college{tbfHv-r-WBvwb1pkFEzKcM6RWjogL2tQHQqe8eJRC0j0N1E}
pwn.college{YqHxczO6W4vQdrpKiCie8OIc3dND-EDH429DSmtLaRPYJT-}
pwn.college{6U2STddETFNYawkWizsB8frMoQuOt-KYzBH5k0OAVPz2xF4}
pwn.college{JcaURziYDe7V63YQ45mb3b.x306hcmH9PyEGdH5XuMopSp8}
pwn.college{Dd8ynWc6LxObLsiJN.p1j151yFoG6ibP5pAH..1jMKUTZAW}
pwn.college{PYpWRdBuBwvDMBo50mJVAdHay4lUoQfUCM4KTCxR0rF4XRv}
pwn.college{s3EMJjMvQOun559mkQvEY6KLP.DVd9cggm97W1zQdG4jpyb}
pwn.college{uysZU4.Ni43anxOe4hGg.nMMzevQ4zUeiXeie2jNZbnJWv5}
pwn.college{Zx-.8S5.5V5CM9SsE.bhyqTspISmARoMWJONI0MNNilzw7W}
pwn.college{pqWDJIBNKbtdwScuS34mM-82yDxX3Almk5uHtBqDVRUfvYp}
pwn.college{WJH5irUQCE0D2HwNipgJ6r2r3l6K0be1nZRep9wsNS3Ncmk}
pwn.college{RS8uTjXbgu50eEY0bvABt6OC4Pd4-c7yejaAWmLWrRGs.eu}
pwn.college{6iMOLljTw1EXxAbw8RpZdxLKxpGKGg2BeXM7Xx3Mr8MfjcZ}
pwn.college{Za5O53TkQaSk9YLwGbsIlgooNKhlLvOhrZPG9mJ.IjjJ4Z7}
pwn.college{.3ot730PnADWowB2A7o2PjfXtSDiJO0K5OiMyYbSVfVGqr2}
pwn.college{vEEV.zQyZScWRGpyP9D9lINWZ-0WgkF6y7cgyZiaWD5rDIQ}
pwn.college{NY6azEjpEim9CdKOMc6YubnkOF01n7RByKyp-Uj0YToJ4iy}
pwn.college{PWP7eeHRHFx2RpF2aBXhe5bYQCOXxfJRoTPFtd1ujvtx1c0}
pwn.college{isCorEr3XadQG6DRW81B9COVPpybXCOl-RaC.1NVQKEs9uB}
pwn.college{YJdz.5yRRKvxkxcNBNb8rDItQwnmac6G.44UINzy-rxrP5x}
pwn.college{wJpk1ZQSVds28X68eqx-yXdKIxABftpFTK0YW4N09vifZkq}
pwn.college{YTD-5R-gTPTtzryZIZStdraV-4EeR6HSEqZjNizbkZgwPa1}
pwn.college{ObGgeVmoOSLadOvbHVl27bSxhP5OaDwUyOTXL5CiZupPgQ-}
pwn.college{Lp4grArE.PKhsHtkuZHJbVKlgmSOugI0hsPIcKwAXdTBaIY}
pwn.college{I4QWPNO7f8m9FLN39y7TD4nz2QKW.D.dodpR28cgeIK2daR}
pwn.college{h-b8.-AQvobfRosWvaFDsPrYECfB2M0XxtYJuiTlfzyZX9U}
pwn.college{iSMyYD6DjNcAY45ppfOWIoSk7UHuktZ5q7TJ-85X.lmozrb}
pwn.college{ItbfuGTmGfa9NDG3c6-PQsEvk8ygXgZEsIewp.UWogfDfU6}
pwn.college{ppSCtpw.5JJwI4kHt4uJUpPkl15k0Y1Y-UEZYYjP6.C.h34}
pwn.college{U2Ialw3GTphlGt.SOQXx8Aer4b4U1Penw6shWxITTJBpg65}
pwn.college{8XVFqHyxuKFib2iVmtUF3qI8jSNkOCBd4h8xv3oByZQCn70}
pwn.college{CtFguXP.C.e5FGsIM4A7yb8XOpbhKT8DYOA5k8JfFTSL1zl}
pwn.college{wEdFCPHiCdxlWfgiKPq5qDsGl7gSsmNEU9dfEaDSPFoyb1S}
pwn.college{6tvouuRoIOyMQxryAMCs3M7tMAa3hsoPoK3kKg-H9nUxxul}
pwn.college{bmvWK-efufNaf1o-ci9EzJJa-SjCPlXat-XDUbTiSBgN3-y}
pwn.college{sJAlYyRDRKYjPjIcHux480YX-lU81fMXyiGamahdn3VGYS5}
pwn.college{XgvUjCDHIQBV8mFJhNvZ4LKh1vGgVH.n3av28pZ7awHLDhb}
pwn.college{ftGaAUf1ke-EHEz9sRihqO8Ohiez97PMYh.0.IaWlHPARrO}
pwn.college{k7PbRrE7YKsyTZE121Kk87MWKyB..hQGYwrZLvT6-nc8-m.}
pwn.college{qZeOY3kE0oNQVU3bomNt4llylT1GDrnqm7.iFUGhJNXlFLB}
pwn.college{FlBAZDk1gdFfPiZSY3UlKcrysQl9RAaXCA1ljR-Wdk8n8.P}
pwn.college{NIx5wZ6M6zGjwqOARF-eWvQ4d-PYmO8YFM9W9xnM0XkhZxR}
pwn.college{QBlAWnbGRJMlw-z1v3i22oh8vSO2LIWKuTSg2q.2dxuBv0n}
pwn.college{e9fqC6r4yx4-5OCxsmf5m-zQe4itFbsItCw1B6nH00dPCea}
pwn.college{3bWBsRXpk5ERFAOp6byO9OonlwBxzgV8qwAidFXPmfcab19}
pwn.college{nW5wqvobsng9PUcw.5TKzM1nq-THPEdx-xWJqmX2xNEmf6-}
pwn.college{kWNcair9KLkAsMSEG7N.u59zkyTVIRTcMdolYe7yihq9y-5}
pwn.college{zBAlrOFFKReJqp1usSva.OtCMYC0UzKCU3cInuBjhm2Lu.X}
pwn.college{uKsMhVmw97wIk0pdtigdisOjO2N4lmlDTSopR6XbnmShY7o}
pwn.college{ASFW6vasTijYYKg3viJHs2MpgKixlYoD6ZRhPtONFfQL.pf}
pwn.college{CA2W2okN2xbjg8hnN3F91yKET-i0FTWxkmM3yeBtA-QozQZ}
pwn.college{gtJ6hUtDoOYxeklk4j4JdjtxdvnBPC.Rjb0iGekiXy8ebj9}
pwn.college{yg.R2oiWIKNcpprqlvd7fciUp1xehiU8pJVML2pCuq2M9yn}
pwn.college{x7zmQLEwKSezqhpq8ryAU9dcp2nQiv4OlwPgIHeaCESXPMs}
pwn.college{tHxYgWdoNrpeduDn2xAKbbnrwdRKRfsqQ7obO5Hoj9wLxCM}
pwn.college{MdACT7UZiDdnsJPQxHuAXDUQSISNN5TTzkJ20VIOg3c44Ts}
pwn.college{9NGbUhrmgRFmrtSvUgulo44tBPD2wlg5IqY0Qxcz-YLhObh}
pwn.college{qfO5Kg0Keak40FxuhCbKpSeTTl7YlmXv2ZA3KndfGFQNFSo}
pwn.college{4SflcKKFlFOB1VCOtMFN.7GmOHqlC0Oul9eEDiUkR3Qq2.o}
pwn.college{6V0vb.OVZFwY7dRSRcAUivPPhSvKyvsLDuuIdfblmyEtLIV}
pwn.college{-ykvi9h6z.9mLw2QUbGfGU.oHl-k0YdcyO5HVvfRxY2b-d3}
pwn.college{SAbH56zdXXDgjv-PjaDiQp26JOCM8-3q1X5-WnHanVvB.M8}
pwn.college{WOXdme0Hur02EjKpHq6578hZfsp3emRfH3NBmiasdcljWh5}
pwn.college{41PNelF8GU4NnwBJXhB88c0UoB5fH2B2HLah7DgyQCM328o}
pwn.college{kTPVfH45GjF267s6Wl4LlvPoufBre719p91blXEFWTS66cC}
pwn.college{zT5Hdq.jA.bq2M1oPwy.I-QUCRd2JONFKlwzxDhEUpIFLiv}
pwn.college{UWdewCfGze9jz2Yd4RWU5f0wR2aN7yjsWy6jZQxTQR6ct98}
pwn.college{FlglK2efiilLsT2fIhl4qrFaEXDQbePAsjTz.gz9p5bcb.O}
pwn.college{6SpP1PYCXvDS.fIx2bELD6C3Habolw9kL9e1SeESUJ1kBtg}
pwn.college{uX5RUuFIQK7ioVcKCUS9N8L6ozzK.w4YmQHhv.c327AT9w7}
pwn.college{ss1aGEHaVPoD2xEXz205fIDBRLcXg8owG5xOUSMvZqnvhYA}
pwn.college{7Gd7mCeIpMHhCuazn.9Bupm047jTLxzbo8DP8oZUJGRDJZF}
pwn.college{I0knkXCpNYcs4HVnH3zal-Pvn6nNmW.nhvFp5pS10QrUo7N}
pwn.college{2q81KmmT6FToUnKuuVBcJqeSlQso0lSQcjKdrAPGocxI3nZ}
pwn.college{XIwKr4VgXqury8ah-DNtR3YkZDIq-he8Ah8mvWtTSWCAnJg}
pwn.college{XVKPCA9VoXMxrZ.zJsrLMbLRLxH7UcXq.se17p8xyQyoOvl}
pwn.college{DAHNlZmYMNygY7Moc6yULhi5VjubC2M81wzOzDIQpHY64kD}
pwn.college{x5JHIeGMUz4zOx5i.ckLQ3gTBi7CuETdX.vpAxzhrPceJVd}
pwn.college{9piC8kNqvEW8KonOIGZN5i1WG4HKqwmfBI9FkYJOlivYaLp}
pwn.college{cORnQWsAOxiFcqgyHAf4lZNHjQjFaoGZPQSBJjw.XAhxeye}
pwn.college{DaAAFTm.FT72N1N47-7UmlUPCAe1IFT9qfTmwdE5wTs.vvE}
pwn.college{L-kusArj1PO2vPaKTR3.I0KTF9R6BJXusoxgOLK.FWQ6Kr1}
pwn.college{OzfDQHRgWsENV8Bkz-r7k-oODLlW04Tb-LLvHGUpD.Ew8Ml}
pwn.college{U7XxLqATNydBI9x4xkeyy0KmRaT6LPWf5vCiFJ9UR9bTXNX}
pwn.college{5Ktr6fYFYlGT9WOouvMDMOoofNtE-ORkUTAcYO07Dh1gpb2}
pwn.college{SIlOj8cOGPXsfxpBPw4OdEGu4IvcJqgnM4z6Cv59yvQ1cTC}
pwn.college{4Kk7c93P3wXLYQ1oNQOqwcF9CrqDCw3KpznpZ9I9r9nyKQK}
pwn.college{z-ZhYxX65vIled9nki4BGwVGn79ymZ7MhJGIbtdwPv5LAVR}
pwn.college{jQUo0Cr5VcPLXg5-Xgi2GBgVQjE3c-oZ0wgm8e9eRr.-Yph}
pwn.college{2LXqechx2w8Zy6YXQS2bEqc8RML2A2TlQbtJQWOEDYlVoZL}
pwn.college{sdMlJQw8-_jzaBkPzIoiKT9XFJC.0FNzMDOxwSNyMzNzEzW}
```
### New Learnings

Sometimes a process will not be able to write into a file because another process has the file open. One way of dealing with such situations is to terminate the process using `kill`.

