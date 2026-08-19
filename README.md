<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name:    Srinivas J         </h3>
<h3>Register Number:  212225230276           </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>


<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

<hr>

### Program

```py
import random
import string

def hill_climbing(target):
    # Generate initial random string
    current = ''.join(
        ' ' if char == ' ' else random.choice(string.ascii_lowercase)
        for char in target
    )

    def heuristic(s):
        # Count matching characters
        return sum(a == b for a, b in zip(s, target))

    print("Initial:", current)

    while current != target:
        best_state = current
        best_score = heuristic(current)

        # Mutate one character at a time
        for i in range(len(current)):

            # Do not change the space
            if target[i] == ' ':
                continue

            for ch in string.ascii_lowercase:
                new_state = current[:i] + ch + current[i+1:]
                score = heuristic(new_state)

                if score > best_score:
                    best_state = new_state
                    best_score = score

        if best_state == current:
            print("No better state found.")
            break

        current = best_state
        print("Current:", current)

    return current


# Target string
target = "artificial intelligence"

result = hill_climbing(target)

print("Final:", result)
```

<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Output:</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>

<hr>

### Output

<img width="457" height="580" alt="Screenshot 2026-08-19 155534" src="https://github.com/user-attachments/assets/a8870b44-6d21-4bff-81de-7ebb5f2d1651" />

### RESULT

Thus the Simple Hill Climb Algorithm Implemented successfully.
