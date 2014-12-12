---
layout: post
title:  "Analysieren SMILES mit Razi"
date:   2014-11-23 23:35:13
categories: Java
---

Razi ist eine neue wissenschaftliche Bibliothek für Java.
Mittlerweile diese Bibliothek kannt SMILES analysieren und eine objektorientiertes Modell eines Moleküls machen.

{% highlight java %}
Reader sr = new Reader();
sr.set("C(=O)O");
sr.process();

Molecule mol = sr.get();
{% endhighlight %}


{% highlight java %}
cd.countAtoms(); // Number of all atoms
cd.countBonds(); // Number of all bonds
cd.countBondsByOrder(2); // Number of bonds with order 2
cd.countAtomsByElement(element); // Number of all atoms which are the same with given element
{% endhighlight %}