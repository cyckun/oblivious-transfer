<p align="center">
<a href="https://www.adjoint.io">
  <img width="250" src="./.assets/adjoint.png" alt="Adjoint Logo" />
</a>
</p>

[![CircleCI](https://circleci.com/gh/adjoint-io/oblivious-transfer.svg?style=svg)](https://circleci.com/gh/adjoint-io/oblivious-transfer)
[![Hackage](https://img.shields.io/hackage/v/oblivious-transfer.svg)](http://hackage.haskell.org/package/oblivious-transfer)

1-out-of-2 OT
=============

Oblivious transfer is central to many of the constructions for secure multiparty computation.
In its most basic form, the sender has two secret messages as inputs, _m<sub>0</sub>_ and _m<sub>1</sub>_; the receiver has a choice bit _c_ as input.
At the end of the 1-out-of-2 OT protocol, the receiver should only learn message _M<sub>c</sub>_, while the sender should not
learn the value of the receiver's input _c_.

The protocol is defined for elliptic curves over finite fields _E(F<sub>q</sub>)_. The set of points _E(F<sub>q</sub>)_ is a finite abelian group.
It works as follows:

1. Alice samples a random _a_ and computes _A = aG_. Sends _A_ to Bob
2. Bob has a choice _c_. He samples a random _b_.
    - If _c_ is 0, then he computes B = bG.
    - If _c_ is 1, then he computes B = A + bG.

  Sends B to Alice

3. Alice derives two keys:
    - _K<sub>0</sub> = aB_
    - _K<sub>1</sub> = a(B - A)_

  It's easy to check that Bob can derive the key _K<sub>c</sub>_ corresponding to his choice bit, but cannot compute the other one.


**References**:

1.  Chou, T. and Orlandi, C. "The Simplest Protocol for Oblivious Transfer" Technische Universiteit Eindhoven and Aarhus University


**Notation**:

_k_: Lower-case letters are scalars. <br />
_P_: Upper-case letters are points in an elliptic curve. <br />
_kP_: Multiplication of a point P with a scalar k over an elliptic curve defined over a finite field modulo a prime number.

tions under the License.
```
