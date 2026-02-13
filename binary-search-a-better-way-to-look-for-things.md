# Binary search: a better way to look for things

**Author:** Jegrami<br>
**Date:** 2024-11-14

<p data-block-key="u9873">You are at a supermarket to get some chocolate bars. The market is large, with many aisles displaying products of different types, shapes, and sizes. You can find what you are looking for by checking every single item in every category of every section. This is called <b>simple search</b> (or <i>linear search</i>).<br/></p><p data-block-key="aord7">For a small list of items, simply going through them one by one to find what you're looking for is the reasonable way to go. But for a large group of things, such as goods in a supermarket, running a simple search would consume a lot of energy and waste a lot of time.</p><p data-block-key="ehk0o">You need a better way.</p><p data-block-key="cdmma"></p><p data-block-key="dalrk">This article is a non-technical introduction to the concept of <b>binary search algorithms</b>. You’ll learn what binary search is and how it compares to simple search. You’ll also learn how to implement the technique in code by writing a simple binary search algorithm in Python!</p><p data-block-key="cg8vb"></p><p data-block-key="d7q9t">Back to our supermarket example.<br/></p><p data-block-key="25hk6">We know that products in a supermarket are often organized into categories, like “Canned Goods”, “Confectioneries”, “Fresh Produce”, etc. So the smarter way to find chocolate bars would be to narrow down your search by going to the specific category in which you would expect to find chocolates, such as the section labeled “Confectioneries”, and begin your search from there. This is similar to how binary search works.<br/><br/>Binary search is an algorithm. An algorithm is a series of steps a computer can follow to perform a task. The task could be a simple one like adding two numbers or a complex one like finding the shortest possible path to a group of five cities in different geolocations.</p><p data-block-key="8liqk">A binary search algorithm enables you to quickly find the position of something in a <b>sorted list</b> of things by repeatedly dividing the list in the middle, narrowing down the possible location of the target item with each split, until the item is found or the list is exhausted.</p><p data-block-key="9pvi2">Our supermarket technique isn’t an exact implementation of a binary search algorithm, but the underlying principle is the same: <b>eliminate irrelevant options to get to your target item faster.</b></p><p data-block-key="2nqs8"></p><h3 data-block-key="fu5kq">The guessing game</h3><p data-block-key="a1h11">One practical application of the binary search technique is in the popular guessing game. Here is an example.<br/><br/>I’m thinking of a number between 1 and 10. Your goal is to guess the number in the fewest tries possible, much like the <a href="https://www.nytimes.com/games/wordle/index.html">Wordle game</a>. With each attempt, I'll tell you whether your guess was too low, too high, or correct.</p><p data-block-key="fbklv"></p><p data-block-key="7rctv">Let’s assume my secret number is <b>9</b>. You could try to guess it by following the simple search approach, considering every single number from 1 through 10, like this:</p>

```bash
Me: I'm thinking of a number between 1 and 10. Can you guess the number?



You: 1



Me: too low



You: 2



Me: too low



You: 3



Me: too low



You: 4



Me: too low



. . . 



You: 9



Me: Correct!
```

<p data-block-key="u9873">But wait, that took you nine tries! In Wordle, you’d have run out of guesses before you got the number correctly.<br/></p><p data-block-key="eus97">Now what if you applied a binary search approach? You know the size of the list is 10, and you also know the list is sorted (binary search works only on sorted lists), so you’d start your guess from the middle:</p>

```bash
Me:  I'm thinking of a number between 1 and 10. Can you guess the number?

    

You: 5



Me: too low



#If 5 is too low, then 4, 3, 2, and 1 are also too low.

#They can be safely discarded. You now have to consider

#only numbers between 6 and 10. So you pick a middle number again.

    



You: 7



Me: too low



# Again, 6 and 7 are out of consideration, remaining numbers from 8 to 10. You pick the middle value.



You: 9



Me: Correct!
```

<p data-block-key="u9873">You got the answer in 3 tries, enough to win a Wordle game! That’s four steps fewer than the linear search approach.</p><p data-block-key="qh3k">This may not seem much at first. But the difference in steps between linear search and binary search increases significantly as the input size grows. That is, as the list gets larger, binary search becomes much faster compared with linear search; the gap in efficiency between the two methods widens considerably.<br/><br/>Consider this next example:</p><p data-block-key="43col">At the time of this writing, Spotify has about 11 million artists on its platform. Imagine you want to search for a particular artist by name. Using the linear search technique, you'd have to look at every name in the database, from first to last. That's 11 million lookups, assuming the target name is the last entry in the database. With a binary search algorithm, however, it would take only about 23 lookups! Note how the difference in performance has widened dramatically as we moved from 10 items to 11 million.</p><p data-block-key="dje3s">But how did I know a binary search algorithm would need only about 23 steps to search an entire list of 11 million names? I explain how in the next section.</p><h3 data-block-key="9ih8q">Big O notation</h3><p data-block-key="4l4l1">To measure the speed (a.k.a., <i>runtime</i>) of an algorithm, computer scientists like to use a technique called Big O notation.</p><p data-block-key="5hmgf"></p><p data-block-key="83pp9">Big O notation is simply a way to tell how much slower an algorithm would run if the size of the data it's dealing with grows. In the above examples, we saw how a simple search algorithm went quickly from 9 steps (when the dataset was just 10 numbers) to 11 million steps (when the dataset increased to 11 million names) , while a binary search algorithm went from 3 steps to 23 steps with the same data sizes. This makes binary search the better technique, especially when the list is <b>large</b> and <b>sorted,</b> because the growth of the data does not affect the speed of the algorithm very much.</p><p data-block-key="4i341">There are several Big O runtimes (you can check out this comprehensive <a href="https://bigocheatsheet.com/">Big O cheatsheet</a>), but for the sake of simplicity,<br/> we'll focus only on the two that are most relevant to this article:</p><ul><li data-block-key="ap69i">O(n) — where <i>n</i> is the size of the list</li><li data-block-key="9erpl">O(log n) — where <i>n</i> is the size of the list</li></ul><h4 data-block-key="ei4h">O(n)</h4><p data-block-key="1ue8m">When an algorithm has an <code>O(n)</code> runtime, we say that it runs in linear time, or <b>n length of time</b>. This means that, as the data size (n) grows, the amount of time the algorithm takes to run also grows linearly. (The 'O' in the formula is just the symbol describing the notation.)</p><p data-block-key="5jujs">So if the list is 10 items long, an algorithm with this runtime might take 10 steps to complete a search on it. If the list grows to 11 million, it might then take 11 million steps. The simple search technique, introduced at the beginning of this article, is an example.</p><p data-block-key="e3u0e"></p><h4 data-block-key="38q22">O(log n)</h4><p data-block-key="epu89">Unlike simple search, an algorithm with<code> O(log n)</code> runtime is said to run in <b>logarithmic time.</b> And the binary search algorithm is an example. But what does it mean for an algorithm to run in <code>O(log n)</code> time? More on that in a bit.</p><p data-block-key="a636v"></p><p data-block-key="8arlq">Before I proceed, two points about logarithms:</p><p data-block-key="1nj5e">First, in Big O, <code>log</code> is always understood to be in <code>base2</code>, so the small <sub>2</sub> is sometimes left out in the expression. When you see <code>log n,</code> you should interpret it as <code>log</code><code><sub>2</sub></code><code>n</code> (i.e., <code>log base two of n</code>).</p><p data-block-key="5mjsd">Second, think of logarithms as the opposite of exponents. For example, the expression <code>two exponent three</code> (<code>2</code><code><sup>3</sup></code>), in logarithm, would be written as <code>log base two of eight (log 8).</code> Why? Because <code>2</code><code><sup>3</sup></code> simply means <code>2*2*2</code>, which is equal to <code>8</code>. Converting <code>log 8</code> back to its exponent can be done by simply asking the question, <i>How many time do I have to multiply 2 by itself to get 8</i> <i>?</i> (Remember, it always in base2.) The answer is three times (2*2*2 = 8). That gives you the exponent <code>2</code><code><sup>3</sup></code>. Logarithms are like the "undo" button for exponents, and vice versa.</p><p data-block-key="fsm4s"></p><p data-block-key="5sq52">Now, going back to our Spotify artist list example. We know that a binary search algorithm runs in logarithmic time. We also know that the Spotify artists databse has 11 million entries. And, based on our knowledge from the second point on logarithms above, <code>log 11,000,000 = 23</code> (2 multiplied by itself 23 times gives you 11 million.</p><p data-block-key="1nap9">So a binary search algorithm would run a complete search on a sorted list of 11 million names in approximately 23 lookups.</p><p data-block-key="81ns6"></p><p data-block-key="a2k9t">Big O helps us compare algorithms to understand how they perform as the data they handle gets larger. It helps us make better decisions on which algorithm to use for specific use cases because, using Big O notation, we can predict how their performance will be impacted as their input size grows.<br/></p>

<h3 data-block-key="fo5h0">Writing your first binary search algorithm in Python</h3><p data-block-key="18kt0">Now that you understand what binary search is, how it compares to linear search,<br/> and how computer scientist and software engineers measure the performance of algorithms, you’re ready to write your first binary search algorithm.</p><p data-block-key="bauaj"></p><p data-block-key="6msph">To follow the code example in this section, you’ll need to have Python and a code editor installed. Get the latest version of Python for your operating system on the <a href="https://www.python.org">official website</a>. For a code editor, VS Code is a popular choice. It’s free, lightweight, and feature-rich. Get it <a href="https://code.visualstudio.com/Download/">here.</a> The rest of this tutorial assumes you have Python 3.13 and VS Code installed.</p><p data-block-key="46dco"></p><p data-block-key="f10ne">A basic binary search algorithm accepts two arguments: <b>a sorted list</b> and an <b>item</b> to search for in that list. If the item is on the list, the algorithm would return its index (i.e., its position relative to other items on the list). If the item is not on the list, the function would return <code>None</code>.</p>

**Note:** <p data-block-key="n074h">I'll use 'index' and 'position' interchangeably in this article. They mean the same thing in this context.</p>

<p data-block-key="am67u">So let's start coding. Open your code editor, create a new file, and name it binary_search.py.</p><p data-block-key="1fga">We’ll start by defining the binary search function we just described above using the def keyword:</p>

```python 
def binary_search(sorted_list, item):
    '''a function to calculate the position of a given item in a sorted list'''
    pass
```

<p data-block-key="fo5h0">The code above defines a function called <code>binary_search</code> that expects two arguments: a sorted list and the item you want to search for in that list. Once these two arguments are supplied, the function will calculate and print out the location (index) of the item you’re looking for. The comment enclosed by ''' ''' is the function documentation (a.k.a, docstring). It describes the function and what it does. The <code>pass</code> keyword is a placeholder for code we'll add later.</p><p data-block-key="5c2m9"></p><p data-block-key="e2h9">In binary search, knowing the exact length of the list is important. So the next step is to set the positions of the first and last items on the list you're working with. This will help you keep track of your search range as you traverse the list:</p>

```python
def binary_search(sorted_list, item):

        '''A function to calculate and return the index of an item in a sorted list'''



        first_item = 0

        last_item = len(sorted_list) - 1
```

<p data-block-key="fo5h0">The position of the last item in a sorted list is simply the length of the list minus 1. This is because, in programming, we use <b>zero-based indexing</b>, where the first item in a sequence is assigned the index 0, the second takes index 1, and so on. So, in a sorted list of 10 items, the last item sits at index 9.<br/><br/>Here's the remaining body of code for the binary search algorithm:</p>

```python
def binary_search(sorted_list, item):



     . . . 





     while first_item <= last_item:  

            middle_item = (first_item + last_item) // 2

            guess = sorted_list[middle_item]

    

            if guess == item:

                return middle_item

            elif guess > item:  

                last_item = middle_item - 1

            else:             

                first_item = middle_item + 1

            # If the loop ends without fining a match, then the item is not on the list, so    

            return None
```

<p data-block-key="fo5h0">A lot of interesting things are going on in the code above. Let’s take it line by line.</p><p data-block-key="5dqgp">After defining the function and marking the positions of the first and last items, we proceed to traverse the list looking for the target <code>item</code>.</p>

```python
while first_item <= last_item:

        middle_item = (first_item + last_item ) // 2
```

<p data-block-key="fo5h0">The first line initializes a while loop that runs as long as the starting index (<code>first_item</code>) is less than or equal to the ending index (<code>last_item</code>). This loop ensures that the search continues until the target item is found or until we reach the last item and exhaust the list. The next line calculates the <b>position</b> <b>of the current middle item</b> by adding the first and last indexes and dividing by 2. The <code>//</code> operator, called <i>floor division</i> in Python, ensures that the result of the division is a single integer value, not a decimal. For example, 5 // 2 returns 2, whereas 5 / 2 returns 2.5. We want a single, definite position. We don't want a "point something".</p>

```python
guess = sorted_list[middle_item]
```

<p data-block-key="fo5h0">Here, the middle item of <code>sorted_list</code> is retrieved and assigned to the name <code>guess</code>. This is our current candidate for the target item. This is the same as what we did in the guessing game example using binary search, where we picked 5, the middle item, as our first guess.</p>

```python
if guess == item:

            return middle_item
```

<p data-block-key="fo5h0">Here we're are checking to see whether our first guess matches the target item. If yes, the function returns <code>middle_item</code>, which should be the index of <code>item</code> in<code>sorted_list</code>. If you want the code to return the item itself, not<i> its position</i> on the list, all you have to do is change the return value from <code>middle_item</code> to <code>item</code>. So the code would now read:</p>

```python
if guess == item: 

        return item
```

<p data-block-key="fo5h0">The next step:</p>

```python
elif guess > item:

        last_item = middle_item - 1

    else:

        first_item = middle_item + 1
```

<p data-block-key="fo5h0">If the number we picked is greater than the target number (<code>guess &gt; item</code>), it means the number we're looking for must be in the lower half of our list. So we narrow our search range to the lower half by bringing our current ending index (<code>last_item</code>) back <b>one position less than the middle</b>, effectively cutting the list in half. But if our guess is less than the target (<code>guess &lt; item</code>), the code also moves the starting index (<code>first_item</code>) forward <b>one position greater than the current middle</b>, discarding the lower half.<br/><br/>For example, assuming our list has 10 items. The target item is 3, but our first guess was 5, which is higher than the target. Invariably, every item after 5 (i.e., 6, 7, 8, and 9) would also be higher than our target and therefore irrelevant to our search. We discard the irrelevant half of the list (5 – 9) by updating the position of <code>last_item</code> to be <code>middle_item minus 1</code>. That would be 5 - 1, which is 4. So our new list now starts at 0 and ends at 4. If our first guess was lower than the target, the algorithm would do the same operation in reverse. Our new list would then start at 5 and end at 9.<br/></p><p data-block-key="e77jm">The last line:</p>

```python
return None
```

<p data-block-key="fo5h0">If the while loop completes without finding the target item, the function returns None. This indicates that the item is not present in the list.<br/><br/>Here's the complete code:</p>

```python
def binary_search(sorted_list, item):

        '''A function to calculate and return the index of an item in a sorted list'''



        first_item = 0

        last_item = len(sorted_list) -1



        while first_item <= last_item:           

            

            middle_item = (first_item + last_item) // 2

            guess = sorted_list[middle_item]



        

            if guess == item:

                return middle_item

            elif guess > item:      

                last_item = middle_item - 1

            else:

                

                first_item = middle_item + 1

            

        

        return None
```

<p data-block-key="fo5h0">Let's run the code to see if it works. We’ll test it on two sorted lists: a list of numbers and a list of desserts sorted in alphabetical order:</p>

```python
>>> numbers = [20, 33, 40, 55, 58, 64, 77, 89]

>>> desserts = ['bacon', 'donut', 'eggs', 'ice cream', 'pizza', 'spam']

>>> print(binary_search(numbers, 77))

6

>>> print(binary_search(desserts, 'ice cream'))

3

>>> print(binary_search(numbers, 90))

None

>>> print(binary_search(desserts, 'cheesecake'))

None
```

<p data-block-key="fo5h0">If everything goes well, you should see results similar to the examples above. The algorithm returns the positions of the items you specify in the first and second print calls. The number 77 is at index 6 of the list <code>numbers</code>, which is why the function returns 6. The same goes for 'ice cream', which is at position 3 of the list <code>desserts</code>. The third and fourth print calls both return<code>None</code> because 90 is not in <code>numbers</code> nor is 'cheesecake' in <code>desserts</code>.</p><p data-block-key="fuhoe"></p><p data-block-key="e1ghh">That's it! You have successfully implemented a binary search algorithm in Python. Although it’s tested here on a small list of items, this algorithm will work perfectly even if the list is one billion items!<br/></p><p data-block-key="9vkal">Don’t stop here. There are many more powerful and important algorithms to learn. This is your first step into mastering skills that are useful for everyday problem-solving. I’m also learning and loving it. Join me!<br/><br/></p>

