# Spectre Attack Demo (i5-3320M and Intel Xeon v3)
This shows my own try of Proof of Concept Exploit demonstrating the [Spectre](https://spectreattack.com/) attack. Unfortunately, I have been able to reproduce it smoothly both on my local laptop and on my AWS Server.

## Exploiting Speculative Execution
According to the Spectre paper,
> Spectre attacks trick
the processor into speculatively executing instructions
sequences that should not have executed during correct
program execution

The two secrets are declared here:
```c
char * secret = "This is some sample sensitive data";
char * secret2= "This is some other sample sensitive data";
```

I first tried it on my **local laptop running an Intel i5-3320M on Ubuntu 16.10 Yaketty**

![local_cpu.png](local_cpu.png)

and it worked, as seen here:

![Spectre_i5_ubuntuYakkety.jpeg](Spectre_i5_ubuntuYakkety.jpeg)

Then, I tried it on my **AWS EC2 Instance running an Intel Xeon E5-2676 v3 on Ubuntu Server 16.04TLS**

![server_cpu.png](server_cpu.png)

and it worked as well:

![Spectre_Xeonv3_ubuntuXenial.jpeg](Spectre_Xeonv3_ubuntuXenial.jpeg)


Seems like we are all [f\*ucked](https://twitter.com/syned/status/948862050306052096).


### Credits
Spectre was independently discovered and reported by [Jann Horn](https://twitter.com/tehjh) and [Paul Kocher](https://paulkocher.com/) in collaboration with, [Daniel Genkin](https://www.cis.upenn.edu/~danielg3/) (University of Pennsylvania and University of Maryland), [Mike Hamburg](https://www.shiftleft.org/) (Rambus), [Moritz Lipp](https://mlq.me/) (Graz University of Technology), and [Yuval Yarom](https://cs.adelaide.edu.au/~yval) (University of Adelaide and Data61).

#### Their great researching work is documented in the [Spectre Paper](https://spectreattack.com/spectre.pdf).
