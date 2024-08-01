---
title: "Identity"
date: 2024-02-26T16:39:42Z
draft: true
katex: false
mermaid: false
description:
---

There's two approaches to thinking about what gives a thing its identity, ie
what makes it itself, or what makes it a member of a certain group. The first
more obvious perspective is that a thing's identity is what it is made of, ie
the matter or information or state that it contains. The other perspective is
that a thing's identity is what it does, ie the actions it can take and the
inputs and outputs of such actions. I suspect that both approaches are equally
valid definitions of identity, but I'm not sure I know how to argue that point.
Instead I will give some examples of where each approach is used and where each
approach is useful.

## Object Oriented Programming

In the object oriented programming (OOP) paradigm, data and code are organized
into objects. An object contains some structured data called members and has
some actions called methods that can be taken on / using the members. [^1](I
believe that the main problem that OOP solves is how to pass context around
between different parts of your program. Here context means state whose scope is
larger than one function but smaller than the whole program, and which is
generally not a primary input or output of the functions where it's used. As a
side effect, the syntax used for OOP in mainstream programming languages allows
us to string together functions from left to right and without nesting
parenthesis. This is an incredibly important benefit which could have also been
gotten through having better syntax in the first place, and which could
theoretically be decoupled from OOP.) Part of the philosophy of OOP is that the
members should generally be private, while the methods should be public. That
is, a programmer using an object should only be aware of what it does, not what
it's made of.

There are a few benefits to this approach. The main one (TODO: fact check) is
that the designer of the object can later restructure the members without
breaking code using the object. Another benefit comes through inheritance, where
different objects with some methods in common can be mixed together and used in
the same way.

I have some problems with this approach. For one, I've had situations in the
past where I needed to access some data inside an object, but the data was a
private member and there was no method to access it. In the end I just had to
use a different library, which was a frustrating waste of time. Also, knowing
what data an object contains is important for understanding the role it plays in
your program. In Rust, the documentation generally hides the members and only
shows you the methods of an object, in order to enforce this philosophy. But I
often still need to see the members in order to understand the object, so I'm
left having to read the source code.

So, this is a situation where the dominant viewpoint is that the identity of an
object should be what it does, but I disagree and think that what it's made of
is often important.

## Tangent and Cotangent Vectors

Here is how I like to explain tangent and cotangent vectors on a manifold $M$.
"Manifold" is a scary word for a familiar concept: a manifold is any space which
locally looks like Euclidean space $\mathbb R^n$, eg paths, surfaces, etc. A
tangent vector to $M$ at a point $p$ represents the derivative of a function
$\gamma: \mathbb R \to M$, called a path. A cotangent vector represents the
derivative of a function $f: M \to \mathbb R$, called a scalar field. There is a
natural product between paths and scalar fields. What you do is you compose them
to get a function $f \circ \gamma: \mathbb R \to \mathbb R$, and then you can
take the ordinary derivative at the point where $\gamma$ passes through $p$:

$$\langle \gamma f \rangle = \frac{d}{dx}f\circ\gamma(x)|_{\gamma^{-1}(p)}$$

Next what we say is that two paths $\alpha, \beta$ have the same tangent at $p$
if this product agrees for all scalar fields $f$, ie $\langle \alpha f \rangle =
\langle \beta f \rangle \forall f$. Similarly, we say that two scalar fields
have the same cotangent vector if they have the same product with all paths, ie
$\langle \gamma f \rangle = \langle \gamma g \rangle \forall \gamma$. We then
define the tangent space $T_pM$ to be the set of all equivalence classes of
paths under this equivalence relation, and the cotangent space $T^*_pM$ to be
the set of all equivalence classes of scalar fields.

Now, these spaces are in fact vector spaces. For the cotangent space there is an
easy way to give it this structure. Scalar fields can be added and scalar
multiplied (ie multiplied by a constant), and these operations commute with the
$\langle\rangle$ product, so they descend to the cotangent space. This does not
work for paths. The reason this works for scalar fields is that when a set has
algebraic operations, you can use these operation on functions into the set by
applying the operation to the outputs, eg $(f+g)(x) = f(x) + g(x)$. The range of
a scalar field has algebra, but the range of a path does not. Its domain does,
but this does not help us. [^2](This is a general phenomenon that covariant
objects are more powerful, because their ranges have algebra and so they have
algebra. Homology is a theory where we ask what happens if we just add paths
anyways because fuck you. Cohomology is the dual theory, and has a product in
addition to addition, for the same reasons mentioned here.) In fact, in general
given two paths there's no obvious way to construct a path whose tangent is the
sum of their tangents.

Instead what we can do is redefine the tangent and cotangent spaces so that the
identity of a vector is the values it takes in the $\langle\rangle$ product.
That is, we can (have to?) take the perspective that a vector's identity is what
it does, not what it's made of. Now for $u, v \in T_pM$ we can define their sum
by $\langle u+v\ f \rangle = \langle u f \rangle + \langle v f \rangle$. We can
similarly define the sum of covectors by how they act on paths. Note that we are
abusing notation by taking products between vectors and scalar fields, paths and
covectors, and between vectors and covectors, although there is a canonical way
to extend the product to these objects.

However, here's an alternative conclusion: we could say that addition is not a
natural operation on vectors, only on covectors. Smooth vector fields are the
Lie algebra of the diffeomorphism group, so if we say that addition is not a
natural operation on the tangent space then we also have to take the perspective
that addition is not a natural operation on Lie algebras. I am starting to
suspect that this is the case. After all, I can't think of a fundamental formula
in Lie theory that uses plain Lie algebra addition with no extra terms. Note
that the tangent space still has scalar multiplication, given by rescaling the
parameter of the paths.
