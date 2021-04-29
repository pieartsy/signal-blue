# Signal Blue
A fork of a fork of [apeper's] Disco Elysium twine macros. The first fork is here: [link](https://github.com/pieartsy/DiscoElysiumTwineMacros-Fork/tree/sample). The link is a mostly-blank template as well as documentation.

This is a Kim-specific version, centered around the idea that Kim thinks in bullet journal fashion.

The three macros you should know about for this version:

# para
You can find this with the same title in the Twine app, or as `para.tw` when using Tweego. It is a tweaked version of `AddParagraph` from the usual template.

It adds paragraphs and dialogue, and you'll probably be using it the most. There are three arguments that you're going to use - the first one is for the text of the paragraph, the second one is for the bullet journal signifier before it, and the third, which is optional, is how much the paragraph is indented by.

After every instance of this macro being used, a `Continue` button will pop up that the user will have to click to move to the next paragraph. Keep this in mind when you write so you can pace well!

An example passage would be:

`<<para "\"Hello!\"" "ev">>`
`<<para "This enby has bright pink hair and an even brighter smile." "ob" 1>>`

This looks like:
![image](https://user-images.githubusercontent.com/17207322/116616347-9d5fcb00-a90a-11eb-8c51-9431d1192c39.png)

The signifiers used are:

☐ - An incomplete task. The abbreviation is "ta" for "task added".

☑ - A complete task. The abbreviation is "td" for "task done".

➤ - A note, something that Kim wants to remember or take note of. It can also be a relevant fact or deduction about a situation. The abbreviation is "n" for "note".

☁ - A thought that Kim has about a situation. The abbreviation is "th" for "thought".

○ - An event, used to describe actions that happen. The abbreviation is "ev" for "event".

◇ - An observation, something Kim perceives with his senses. The abbreviation is "ob" for "observation".

‼ - Something deemed highly important by Kim. The abbreviation is "im" for "important".

To indent by 1 em-dash, write 1 for the third argument. For 2 em-dashes, write 2, and so on. These numbers are standalone; they don't need quotes.

Note: If an argument contains text, then you need to put it in double-quotes. If you want to have dialogue, you will need to escape any double quotes you wish to appear in the text itself, \"Like so\". (Escaping a character in Twine means that it's counted as plaintext/part of the visible writing, not part of the code itself).

# flag
You can find this macro with the same title in the Twine app, or as `flag.tw` when using Tweego should you want to edit it. It sets a flag, also known as a variable. You can use it to keep track of aspects of the game that are variable depending on which option you pick, as well as any items that the player picks up. It takes two arguments - the first is the name of the flag, and the second is the value stored in the flag.

Example:

`<<flag "blue pen">>`

Here, `blue pen` is the first argument (the name of the flag), which will automatically be added to the array, or list, of flags.

`flag` and flags in general are used with the if macro, which is built into Sugarcube. You can find more info about if and other control macros at the Sugarcube docs: link. In this code, the if statement will look something like this:

`<<if $flags.includes("blue pen")>>
    <<para "You have a blue pen." "ob">>
<</if>>`

`flag` also interacts with the `opts` macro.

# opts
You can find this macro with the same title in the Twine app, or as `opts.tw` when using Tweego should you want to edit it. This is how we give the player options that influence the outcome, and thus make the game truly interactive. The `opts` macro can take in 3 arguments. The first argument is the text of the option, and the second argument is the passage the option sends you to. That's the bare minimum you need to create an option.

Example option:

`<<opts "Take the pen while no one's watching" "Steal pen">>`

Here, `Take the pen while no one's watching` is what the player sees, and `Steal pen` is the passage that they're sent to.

You can also add a third argument, which does the same thing as the `flag` macro, adding a variable to the `flags` array.

`<<opts "Take the pen while no one's watching" "Steal pen" "blue pen">>`
