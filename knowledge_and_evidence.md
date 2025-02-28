<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Directory Structure (INSERT YOUR SCREENSHOT)](screenshots/directory-structure.png)

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/local-execution.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name   | value           |
   | ----------              |--------|-----------------|
   | built-in primitive type | dimmed | True            |
   | built-in composite type | WHITE  | (255, 255, 255) |
   | user-defined type       | smiley | Happy()         |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type   |
   | ------------             |--------|
   | self.pixels              | list   |
   | A member of self.pixels  | tuple  |
   | self                     | Smiley |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File      | First line | Line range |
   | ------------ |-----------|------------|------------|
   |  sequence    | smiley.py | self.sense_hat = SenseHat()         | 13-26      |
   |  selection   | sad.py    | if wide_open:         | 26-30      |
   |  iteration   | happy.py  | for pixel in eyes:         | 30-31       |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example                 |
   | ----------------------- |-------|-------------------------|
   | int                     | Yes   | eyes = [10, 13, 18, 21] |
   | float                   | Yes   | delay=0.25              |
   | str                     | No    | jake = "awesome"         |
   | bool                    | Yes   | dimmed=True             |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> The colour variables such as 'WHITE' are class variables as it is defined within the class, but outside of any methods so it is set for all instances of the class. By comparison, there is 'self.sense_hat' which is an instance variable as it is defined within the '__init__' method which means it will assign a new/unique attribute for sense_hat for each instance that is created.
>

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > A constructor is used to create a new instance of a class with specific attributes, in this case it will create a new instance of the class Happy, inherit the attributes and methods of the 'Smiley' and 'Blinkable' classes and call the self.draw_mouth() and self.draw_eyes() methods defined within the Happy class which are methods defined within the Happy class that display the mouth and eyes of the smiley in a specified way.
   >

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > On initialization it will call the __init__ methods from the parent classes, given only Smiley has an __init__ method it will call that first along with anything within that method being executed, it will then call the methods defined within the class 'Happy' __init__ method which are draw_mouth() and draw_eyes() which will complete the initialization of a new instance of class Happy.
   >

### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:
   
> PEP 8 is the style used. Yes it is likely the style used in SenseHat is PEP8 given the class 'SenseHat()' is correctly formatted with CamelCase, and methods are labelled using snake_case when called in smiley.py such as 'set_pixels()'. It is also the universally accepted style for Python programming due to readability and also maintaining consistency throughout projects or even the industry as a whole in regards to Python.
>

2. List three aspects of this convention you see applied in the code.

> - Within the class Smiley, the colour variables are labelled in all upper-case as they are not meant to be re-assigned. They are considered constants.
> - Variables are written in snake_case, for example 'dim_display'
> - Two empty lines above classes to separate them from other sections of the code.
>

3. Give two examples of organizational documentation in the code.

> Your answer here
>- Docstrings used to explain methods such as with the 'show' method within the Smiley class.
>- Comments used for additional useful information such as within the init method in Smiley class indicating that there are protected attributes within the SenseHat object.

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s)  |
|------------|---------------|-------------------|
| Smiley     | Super         | None              |
| Happy      | Sub           | Smiley, Blinkable |
| Sad        | Sub           | Smiley            |
| Blinkable  | Sub           | ABC               |
| ...        | ...           | ...               |


2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction is essentially hiding the inner workings of a function, only showing the user what they need. For example, within the Blinkable class we have the blink() abstract method defined. This shows what any instance of a class that inherits from Blinkable should be able to do, but not how they do it.
>

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> Deriving from base classes refers to 'Inheritance'. For example in this project we use this to build upon the default state generated by the Smiley class with additional methods contained within sub classes. For example, the Sad class is a sub-class of Smiley, which allows you to create an instance that uses everything from the Smiley class, but also adds its own attributes on initialization as defined in its draw_mouth() and draw_eyes() methods.
>

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > Happy has two parent classes (Smiley and Blinkable), whereas Sad only has one (Smiley).
   >
2. What are the key similarities?
   > They both have draw_mouth() and draw_eyes() methods
   >
3. What difference stands out the most to you and why?
   > Sad does not have a blink() method and does not inherit from the Blinkable class.
   >
4. How does this difference affect the functionality of these classes
   > Because Happy inherits from Blinkable it must have a blink method defined, which allows it to make the face blink. Whereas Sad can not make the face blink as it has no such method defined.
   >

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > Smiley, Happy and Sad.
   >
2. Which of the SenseHat's functionalities do(es) it/them utilize ?
   > SenseHat() is called and assigned to 'self.sense_hat' within the Smiley class, and then this variable is used within the dim_display() and show() methods which adjust the light intensity and display the smiley respectively. Both Happy and Sad inherit these methods.
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > Encapsulation is the concept of hiding the inner workings of something and only revealing through an interface access to the capabilities within the class. This helps to protect the functionality of the class, and also simplifies utilization of it as you don't necessarily need to know how it all works behind the curtain. Such as driving a car, without needing to know how it runs under the hood. 
   >

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> Yes, as the class Happy is inheriting from the Blinkable class, it also inherits the abstractmethod blink(), which means a blink method must be defined within the class.
>

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> No, as the blink() method is only defined as an abstract method within Blinkable(), it is required that each sub class define it individually, and as such it would be expected that some or all will function differently to one another.
>

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> Polymorphism refers to the idea of being able to implement methods of the same name across classes that can behave differently based on the object that they are interacting with. For example, the blink() method which has been defined as an abstract method within the Blinkable class, has then been inherited by the Smiley class and had unique behaviours set for when that method is called for instances of Smiley. Whereas Sad has not defined the blink() method, and is not required to since it has not inheritated the abstract method from Blinkable.. but if it had, then it would need to define the behaviour of the blink() method for when it's called upon an instance of Sad. This is essentially what polymorphism is, the same method having unique characteristics based on the object that it's called on.
>

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> Within the blink method the self.show() method is called, which is a method that has been inherited from the class Smiley.
>
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25):
       pass  # Replace 'pass' with your implementation
   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![Sad Smiley Blinking](screenshots/sad-modified-main.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > As per the class Happy, Sad now also does a single blink, but I have increased the duration using the delay argument, in order to use the value assigned to delay, I needed to pass it through the method time.sleep() which required me to import the time module.

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > Blinkable is an abstract class.

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > It's an interface. It's defines what classes that inherit from Blinkable must be able to do, but not how they do it.

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > This represents Abstraction, as it shows what objects associated with Blinkable can do, but hides how they do it.

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > Because the class Blinkable only serves to force a sub-class to define blink(), but you can still define methods of the same name as used in other classes with their own unique functionality for instances of the class they are defined within. 

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > This is called Duck Typing. Python and other dynamically typed languages do not need you to define what something is, only what it does ('if it quacks like a duck, then it's probably a duck'). Where in Python you can have the same method in two different classes independently, in statically typed languages you must explicitly state that these classes can both support this method. Using blink() as an example, in a statically typed language you would need to inherit from Blinkable to use it, but in a dynamically typed language you don't.

  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > We have White, Green, Red, and Yellow defined within the class Smiley and these are inherited by sub-classes of Smiley (Happy & Sad)
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > These are class attributes/variables, and given they are in all capital letters, it is assumed that they are constant and will (or should) never change.
     3. Add the color blue to the appropriate class using the appropriate format and values.

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > The colour variables are inherited by and used in the Smiley, Happy and Sad classes.

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > Changing the value assigned to Y would probably be the easiest way, for example changing it from 'Y = self.YELLOW' to 'Y = self.GREEN' within the init method of Smiley. This would also need to be adjusted within the draw_eyes() function in both the Happy and Sad classes.

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

  ![Bulk Rename](screenshots/refactor-grid.png)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

    ### Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***
