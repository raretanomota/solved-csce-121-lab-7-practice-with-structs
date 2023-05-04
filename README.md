Download Link: https://assignmentchef.com/product/solved-csce-121-lab-7-practice-with-structs
<br>
This lab will give you some practice with structs and also with problem solving, requiring some of the previous ideas, possibly combining them in fresh ways.

Advice on managing your lab time

The two questions emphasize different things, so try to be strategic: use your lab time for the things that you think you’ll need the most help with.

<ul>

 <li>The vanishing subsequence question involves some conceptual challenge, but doesn’t require many lines of code to be written. It is like a short steep run, it’ll check that you have the requisite (mental) muscle power.</li>

 <li>The triangles question is conceptually straightforward, but will take a bit of time to write all the functions needed. If you find yourself writing code that is very similar in multiple places, or even copying-and-pasting, this is a sign that you should stop and think about how to refactor your program. It’ll require a bit of stamina, but mainly a keen sense of the overall picture (which is sort of like pacing).</li>

</ul>

In both questions you can benefit from some pre-planning. You might find it helpful to start with a pencil and paper, before hitting the compiler.

Is there a vanishing subsequence?

Given a sequence of numbers, is there a (non-empty) selection of those elements that sums to zero? Write some code that, given an array of ints, will report whether it is possible to find such a selection of elements.

Calling your function as in the main() in the following snippet:

#include &lt;iostream&gt;using namespace std; … int main(){    const int n = 7;    int listA[] = {1, 7, 4, -5, 3, -2, 9};     cout &lt;&lt;; “List A: “;    sums_to_zero(listA, n);     int listB[] = {24, 14, -2, -10, 7, -3, -17};    cout &lt;&lt; “List B: “;    sums_to_zero(listB, n);     return 0;}

should produce the following output:

List A: 1 4 -5 List B: It isn’t possible, sorry!

<table>

 <tbody>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td>

    <table>

     <tbody>

      <tr>

       <td>There are several ways to approach this problem. The ideas from both the McNugget numbers exercise and the phone numbers exercise are applicable.</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

<h2>Triangles and their associated properties</h2>

In this question, we’ll write some code to represent and answer particular queries about triangles.

<h3>Types to represent the data</h3>

We represent a triangle via its three endpoints; first we define a structure to represent a point. For this exercise, assume that the points are integers:

struct point_t { // Points with integer coordinates    int x;     int y;};

Now we can define a type to represent triangles:

struct triangle_t {    point_t pt[3]; // Three points define a triangle};

That should allow you to define some triangle like this:

int main(){// Make sure you understand why are there three levels of braces, rather than two in the following:        triangle_t t1 = { {{0, 0}, {3, 0}, {0, 4}} };         triangle_t t2 = { {{90, 0}, {90, -4}, {87, 0}} };         // Do stuff with my triangles        //  . . .         return 0;}

Write a function to print out a triangle_t.

<strong>Important!</strong> Read through the rest of the question now. Each bit below describes some new functionality that will be needed. Once you’ve read through to the end, you’ll be able to plan ahead; think about what functions you can write once and reuse—common helper functions can make coding faster, easier, and less error-prone.

<h3>What sort of triangle is it?</h3>

Before looking into more complex properties, we should check that the three points do actually make a triangle.

<table>

 <tbody>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td>

    <table>

     <tbody>

      <tr>

       <td>I found that the order_triple function from an earlier lab was rather useful.</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

bool isdegenerate(triangle_t tri){ // Are the points distinct?    . . .}

Perhaps we’d like to know if the triangle is right-angled in order to use trigonometric functions with it. Write a function to ascertain whether this property holds.

bool isright(triangle_t tri){ // Check whether the triangle has a 90 degree angle    . . .}

<h3>How do two triangles relate?</h3>

In this question we’ll consider three different notions of equivalence:

<ul>

 <li>Two triangles are <em>identical</em> if they describe the same geometric shape and are in an identical position.</li>

 <li>Consider two triangles are considered to be <em>congruent</em> under the usual <a href="https://en.wikipedia.org/wiki/Congruence_(geometry)">Euclidean geometric definition</a>.</li>

 <li>And, also we’ll consider triangles to be <em>similar</em> under the <a href="https://en.wikipedia.org/wiki/Similarity_(geometry)">standard definition</a> of Euclidean geometry.</li>

</ul>

For each of these three, write a function that takes two triangle_ts as parameters and returns true if and only if they relate in the specified way.

<table>

 <tbody>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td>

    <table>

     <tbody>

      <tr>

       <td>If you need the declarations of the functions as a starting point, they are available <a href="http://robotics.cs.tamu.edu/dshell/cs121/l7/tris_hint1.cpp">here</a>.</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td colspan="2">

    <table>

     <tbody>

      <tr>

       <td>Still stuck? The comments in <a href="http://robotics.cs.tamu.edu/dshell/cs121/l7/tris_hint2.cpp">this file</a>. give away all the nuance in the question. It is probably best not to look at this until you’ve made a serious attempt on your own.</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

What is the relationship between these three functions?

<table>

 <tbody>

  <tr>

   <td>

    <table>

     <tbody>

      <tr>

       <td><strong>?</strong></td>

       <td>HINT</td>

      </tr>

     </tbody>

    </table></td>

   <td>

    <table>

     <tbody>

      <tr>

       <td>Answer in the form: “If  <strong>tri<sub>1</sub></strong>  and  <strong>tri<sub>2</sub></strong>  are  ________  then they are  ________ .”</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

Mathematically an <a href="https://en.wikipedia.org/wiki/Equivalence_relation">equivalence relation</a> describes a special type of relationship between two objects, which accords with our intuitive idea of how some notion of <em>alikeness</em> ought to behave. If ≡ possess the following three properties, then it is an equivalence relation:

<ol>

 <li>For every object <em>X</em>≡<em>X</em> (reflexive property),</li>

 <li>if <em>X</em>≡<em>Y</em> then <em>Y</em>≡<em>X</em> (symmetric property),</li>

 <li>and if <em>X</em>≡<em>Y</em> and <em>Y</em>≡<em>Z</em> then <em>X</em>≡<em>Z</em> (transitive property).</li>

</ol>

Which, if any, of the three notions of alikeness among triangles is an equivalence relation.

Test cases

Invent some test cases to evaluate the functions you’ve written. (It is actually most helpful to do this while writing the functions, not just at the end.) Try to make them tricky. Exchange test cases with your peers and see if your code agrees with theirs. Also, consider posting them on piazza to help others testing their code.

Solving it multiple ways*

The vanishing subsequence question can be solved recursively or in an iterative form. It is good practice to attempt it both ways, as the challenges are quite distinct.


