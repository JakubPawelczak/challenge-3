# Challenge 3 - Views

**Congratulations on completing the second challenge!**

In this exercise we will teach Bixby how to show the results that it found!

1. Download the capsule code for this challenge.

2. Look around, get familiar with the capsule - Startup Search!

3. Launch the simulator

4. Click on compile!

5. Write the sentence: **what is the golden standard**. Click **Run NL**
Bixby found something great... well... not quite. We see some generic text in a table. Some cut off text, a name and an url of an image. This doesn't feel like good User Experience right? Well Bixby is lucky to have us! Let's help him show this information in a better way!
We define layouts in Bixby using so called **Views**!
We use a set of building blocks to create different cards.
Among those are _cards_, _carousels_, _lists_ and others.

Today we will create an **image card** and a **paragraph**.

5. Jump to code/startups.js -there you can find our mockup database of startups!

6. Each startup contains a few values: 

| GoldenStandard | |
| ------:| -----------:|
| name | The Golden Standard |
| desc | When it comes to gold, we know where to find it |
| url | /goldenstandard.jpg |
>
It would look great if Bixby would show the image of that startup with it's name and description.
We will show the image and the name of the startup in the **image-card** and place the decription within the **paragraph**.

7. Let's create the file: Go to resources/base -right click - new -View Let's call it _Startup_ to know right away what it we're using it for.
We will keep all the setup fields as default, feel free to ask one of us what are they for.

8. Now we have an empty file called Startup.view.bxb
Let's get into coding!
First we will define the view and to which model it is related.

9. Our view will be shown as a result of an action.
Write _result-view {}_ (Add a new line between the braccets to write inside them)

```
result-view {

}
```

10. It will be matched to our Startup model. 
Write _match: Startup_ between the braccets. It tells bixby to use this view when trying to show a Startup model, which he found as a result of an action.

```
result-view {
  match: Startup
}
```

11. We will want to access the fields in our structure so we will add a name to ease our coding later.
let's add _(this)_ after _match: Startup_

```
result-view {
  match: Startup (this)
}
```

12. Now we will start with the building blocks of our UI.
below our match declaration write _render{}_ within this field Bixby will now to render something on the screen.
(Add a new line between the braccets to write inside them)

```
result-view {
  match: Startup (this)
  
  render {
  
  }
}
```

13. Now we want to make sure that Bixby shows our view only if the action returned a Startup structure. (Something could go wrong in the javascript code that we didn't predict!)
Write an if statement like so: _if (exists(this))_ (remember _this_ is our Startup)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
    
    }
  }
}
```

14. Now we will create a **layout**. Write _layout {}_ (Add a new line between the braccets to write inside them)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
      
      }
    }
  }
}
```

15. Within our layout we will have a **section**. Write _section {}_ (Add a new line between the braccets to write inside them)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
        
        }
      }
    }
  }
}
```

16. Our **section** has some **content**. Write _content {}_ (Add a new line between the braccets to write inside them)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
          
          }
        }
      }
    }
  }
}
```

17. And within this **content** is our **image-card**. Write _image-card {}_ (Add a new line between the braccets to write inside them)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
            
            }
          }
        }
      }
    }
  }
}
```

I hope that at this point you got a hang on creating building blocks. So far we've been defining blocks within blocks.
Now it's time to add our image and startup name to the **image-card**.

18. An **image-card** constist of a **title-area** and an **image-url**. Additionaly we will define the text-position to lay over the image.
Write _text-position (Overlay)_ then in a new line _title-area {}_ and in the next line _image-url ("")_

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {}
              image-url ("")
            }
          }
        }
      }
    }
  }
}
```

19. Within our image our we want to pass to Bixby the value of the image url that we have in our Startup structure (look at point **6**).
We write this within the "" braccets of _image-url ("")_ like so: _#{value(this.url)}_
_#{value()}_ defines that we will access some value.
_this.url_ specifies that we want to access our startup (look at point **11**) and within our startup the url field (look at point **6**).

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {}
              image-url ("#{value(this.url)}")
            }
          }
        }
      }
    }
  }
}
```

20. Okay let's define our **title-area**.
Like in points **14** to **17** define a **slot** in our title-area it will be **slot1** (a title-area can have up to 3 slots: slot1, slot2, slot3)
Within our slot define a **text** block. (Add a new line between the braccets to write inside them)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {
                slot1 {
                  text {
                  
                  }
                }
              }
              image-url ("#{value(this.url)}")
            }
          }
        }
      }
    }
  }
}
```

21. Our text needs a **value** and some **style**
Write _value ("")_ and in a new line _style ()_

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {
                slot1 {
                  text {
                    value ("")
                    style ()
                  }
                }
              }
              image-url ("#{value(this.url)}")
            }
          }
        }
      }
    }
  }
}
```

22. for the actual value of our text we want to have the name of the startup.
Just like in point **19** write _#{value(this.name)}_ to access our startup and the field _name_ within it.

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {
                slot1 {
                  text {
                    value ("#{value(this.name)}")
                    style ()
                  }
                }
              }
              image-url ("#{value(this.url)}")
            }
          }
        }
      }
    }
  }
}
```

23. The _style_ of text is a set of predefined font sizes.
We can choose from multiple styles which you can read more about [here!](https://bixbydevelopers.com/dev/docs/reference/type/layout-macro-def.content.text.style)
Let's go with _Title_L_ We want the name of the startup to be big and visible. :)

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {
                slot1 {
                  text {
                    value ("#{value(this.name)}")
                    style (Title_L)
                  }
                }
              }
              image-url ("#{value(this.url)}")
            }
          }
        }
      }
    }
  }
}
```

24. Launch the simulator

25. Write the sentence: **what is the golden standard**. Click **Run NL**

26. Time to apply all the knowledge that you've learned!
Still within our **content** add a **divider** and a **paragraph**.
The **divider** is an empty block without any parameters so it doesn't require braccets
The **paragraph** requiers a **value** and a **style**

> HINT: I would go for a **medium sized detail** style
>
> HINT: for the value look up point **22**
>
> HINT: fill in the **BLANKS**

```
result-view {
  match: Startup (this)
  
  render {
    if (exists(this)) {
      layout {
        section {
          content {
            image-card {
              text-position (Overlay)
              title-area {
                slot1 {
                  text {
                    value ("#{value(this.name)}")
                    style (Title_L)
                  }
                }
              }
              image-url ("#{value(this.url)}")
            }
            BLANK
            BLANK {
              value ("BLANK")
              style (BLANK)
            }
          }
        }
      }
    }
  }
}
```

27. Run the simulator and show us your **view**!