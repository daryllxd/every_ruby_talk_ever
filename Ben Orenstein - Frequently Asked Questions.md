## Ben Orenstein - Golden Gate Ruby Conference 2013: Frequently Asked Questions

#### Pair.
- The best way is to pair with programmers, because you get to learn. If you pair with people who are less experienced, you get to explain things and you get to know what is really supposed to happen.
- "Actually, I don't know. Let's find things about it."

#### Struggle on your own.
It is easy to doubt your own ability and ask if other people struggle on this. This is normal because programming is hard. Do plenty of struggling on your own but don't feel bad. It's going to take a long time, it's going to be hard, that's the way it's supposed to be. 

And you should be struggling. When things are easy, you aren't improving. If you feel that what you're doing is easy, then do something harder.

#### Admit when you don't understand something.

I just made this decision 2 years ago to just admit things when I don't understand them. In this industry, we are intellect-powered. "How smart is that person?" There is this tremendous pressure to maintain a perception. It's super like "oh yeah, whatever". But don't do that. You trade temporary perception for a chance to actually learn.

The more you are embarassed that you don't know something, then the more you should really study it. (Protocol buffer: Used over JSON when you have 2M transactions/second.)

#### Heuristic to Know if You Are Getting Better

I think the most important is to know: How hard is it to change this code? What is it about writing this code a month ago that is making it easy or hard to change.

Oftentimes, duplication is bad. Law of Demeter is about Structural Duplication. You make the change in one place only.

Test code is code too, so it has to be DRYed up. Treat it better than production code because it has no tests. I think you can get clarity without duplication.

#### Make Friends

THe best jobs in the world are passed through word-of-mouth. So I think it is important to maintain friendships (people you like to spend time with).

#### Underpaid

If you think you are underpaid, you are. if you feel that the value you are providing to the company is low, then you are definitely underpaid.

Just ask people for stuff, it usually works. The only thing you need to know is to pass the Giggle test. If you can say a number and you would, and they would not laugh out loud.

If you ask for something and they say no, that's how you maximize your value. The most important thing a salary can do for you is to make you forget about it.

## Ben Orenstein - ArrrrCamp 2013: Frequently Asked Questions

- When you pair with someone better, you learn.
- When you pair with someone who's not as good as you, you learn something by teaching.
- Pair with others. There is no better way to get better.
- Continue to struggle with things. And when everyone is starting, it seems like it is super hard for them, it is hard for everyone.
- *Admit you don't understand something.* Just do the habit of "When I don't understand something, I will just ask what it is."
- When you say "Oh yeah I got it", you trade an opportunity to understand something to make it look like you understand it when you don't.
- When you are super embarassed to admit that you don't know something, that is the best time to do it. When you have the voice in your head that says "wow, I really should know this." And you should. You should admit that. People that make fun of you and give you a hard time when you admit ignorance of something are bad people.
- When that happens, the problem is with them. They have screwed up. I found that the best programmers are willing to understand that "that happens." It's a hard thing to admit that you don't know it.

#### What's a good heuristic to know if you are succeeding?

My favorite heuristic to know how I'm progressing as a programmer is "how easy is it to change my code?" How flexible is this code when you have to change it later. Methods short, classes focused, but the real test comes three months later, when you need to change something. Make sure you bring yourself a level of abstraction up. Do I need to make changes in a bunch of places, which indicates duplication? Pay attention to that.

#### What does this command do?

    history | awk '{a[$2]++}END{for(i in a){print a [i] " " i}}' | sort -rn | head -20

Check your CLI history, awk and pipe, and sort in reverse order.

The motion is a waste of time. The act of typing means that you already know what you are thinking of ("I want my code to look like this now"). The time you spend typing is wasted time. This is the time where you have to spend these muscle motions to inform this fast processor what you want it to do. So I'm constantly looking for ways to shave away keystrokes in time off my workflow.    

`g: git`. Bind the `git` command to tell you to do git. `gad`: Git add entire directory. `gcm`: Git commit with a message.

Pairing: It's hard. DVORAK keyboard and I remapped Caps Lock to Esc.

Whether you are looking for a job or not, it's awesome to have friends who also know Ruby. This is what conferences are good for. You should make friends in conferences.

"Am I underpaid?" The answer is yes, you are, because if you feel that you are uncompensated, then that is when you are really underpaid. If you worry about it, you are underpaid. You can ask your co-workers how much money they make. Though there is a taboo to talk about stuff, but you lose because there is an information asymmetry. *The person who has more knowledge in a negotiation wins the negotiation.* I think we should be much more willing to discuss salary with our coworkers. At least you get things out there.

TDD is the best and most important thing I've ever done for my career. First, it's not that bad. The best way to do this is to pair with someone. When you get to a roadblock ("I'm having trouble testing this"), some of it is because you are inexperienced, but some of it is because there is bad code. Code that is hard to test is definitely a smell. So yes you should design your code to make it easier to test.

My advice for switching to Vim is don't do it. Don't do it at first. When you are still intimidated about what you want to learn, don't do it, you have to optimize your learning speed over the speed number.

Second, use vimtutor. Read "How to surive the first week in Vim." First, relative number. Delete inside Ruby block. Leader commands.

When you also say "you know it" already, you are also hurting the person who wants to teach you something.

