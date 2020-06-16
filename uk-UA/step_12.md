## Using different emojis

You will see that lots of the incidents are not to do with dog poo - they are actually to do with dropping litter. Let's add a different emoji depending on the type of incident.

- Save a suitable emoji image to mark litter being dropped. The emoji should be saved as `litter.png` and it should be saved into the same folder as your webpage. If you want to, you can use [this one](resources/litter.png) from [Wikimedia Commons](https://commons.wikimedia.org/wiki/Emoji).

- Add an 'if' statement to check the type of incident. If it is litter, change the variable to use the litter emoji. Otherwise, we will stick with the default poop emoji.

    ```javascript
    if(data[i]["Contravention_Description"].toLowerCase() == "leaving litter"){
        emoji = 'litter.png';
    }
    ```

    We have converted the `Contravention_Description` to lowercase because some of the descriptions in the data say "Leaving litter" and some say "Leaving Litter". Although a human can understand that these both mean the same thing, the computer thinks they are different. We convert the description to all lowercase and then compare it to the phrase "leaving litter" in all lowercase, so that capitalisation doesn't matter.

- Save your code, then go back to the web browser and refresh the page. You should see two different types of emoji to show different types of incident.

    ![Leaving litter](images/multi-emojis.png)

- The finished code is [here](https://raw.githubusercontent.com/raspberrypilearning/poo-near-you/master/code/worksheet2.html) for you to have a look at.

