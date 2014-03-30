# Cascadia Ruby 2012 - Therapeutic Refactoring Large 

Few things draw my attention than a looming deadline. Some part of my brain watches in morbid fascination as the deadline approaches, wondering whether to call emergency services or maybe just settle in, eat popcorn, and enjoy the show. I can't help but keep a weary eye on it. A weary eye that is no longer paying attention to the code at hand. I need all the weary eyes I can get. Without I forget best practices, I revert to less successful strategies, like guessing, and desperately copying code from Stack Overflow.

Sometimes I'm happy. There are moments when the world melts away. Your sense of self dissipates, you become completely absorbed in what you do. Time appears to slow down and speed up simultaneously. Being awesome feels effortless.

I've taken to coming into the office early in the morning and committing random acts of refactoring. Some people are calling this guilt-driven development (laughter), but really it's not. Refactoring makes me happy. More refactoring is an optimization. So today I'm going to tell you a story. It has a beginning, 2 middles, an end, and a moral.

So to be clear, when I say refactoring, I mean small, careful steps that improve the structure and readability of the code without changing its behavior. Tests are implied.

So, once upon a time, there was an application that performed some incredibly dirty hacks in order to put the data straight into a number of real world, hard copy publishing systems. I found this particular specimen in the dark recesses of that code base:

    def self.xyz_filename(target)
      # File format:
      # [day of month zero-padded][three-letter prefix]\
      # [kind][age_if_kind_personal],[target.id]\
      # [8 random chars]_[10 first chars of title].jpg
      filename = "#{target.publish_on.strftime("%d")}"
      filename << "#{target.xyz_category_prefix}"
      filename << "#{target.kind.gsub(". ","")}"
      filename << "_%03d" % (target.age || 0 ) if target.personal?
      filename << "#{target.id.to_s}"
      filename << "#{Digest::SHA1.hexdigest(random(10000).to_s)[0,8]}"
      truncated_title = target.title.gsub(/[^\\[a-z\]]/i, '').downcase
      length = trunctated_title.length
      truncate_to = length > 9 ? 9 : length
      filename << "#{truncated_title[0..(truncate_to)]}"
      filename << ".jpg"
      return filename
    end

It was in a module that was over 300 lines long, most of which was in a single method. This module talked to code all over the application. It dealt in temporary files, FTP, it shelled out EXIF 2 metadata into JPEG, it handled encoding. It had a comment in it that read, "A kitten dies every time this code is run." (laughter) We had it running on a cron job (laughter). It had no tests and it had no documentation.

The comment is bad, and its wrong. Basically information is being shrugged onto a string, but there is a chunk of something (`truncated_title`). There are also low-level shit such as gsub.

Nothing in the lower level of abstraction make sense. The thing with big ugly code is to break it down to small ugly code.

To start testing, just try to put stuff in anyway. expect anything. First error, no `publish_on` at line 6. We can stub out EVERYTHING to make the object "work".

First failure will look like this:

    let(:target) do
      messages = {
        :publish_on => Date.new(2012, 3, 14),
        :xyz_category_prefix => 'abc', 
        :kind => 'unicorn',
        :personal? => false,
        :id => 1337,
        :title => 'magic & superglue'
      }
      stub(:target, messages)
    end

We got this thingie from just seeing all the methods being called on the thing.

To pass, use a regex for the random part. Fix low-level details, and the alternate paths need test cases (conditionals need this).

So we expand from `it works` to...: `it leaves square brackets`, `it personalizes (basedon the personal conditional)`, `it handles nil age (based on the age conditional)`, `it handles short titles (based on the truncate conditional)`. If we pass everything, we have protection against regressions.

Now we have fake assertions to get us inputs to give us outputs to give us assertions. XD

## Refactoring

*replace method with method object*

[TODO]

Extracting stuff: Identifying a piece of code that performs a subtask and giving the code a name.

## Code Junk
1. Lousy comments: States obvious shit.
2. Trailing whitespace. Problem in either code or the git diffs.
3. Commented code. Just delete stuff if it's supposed to be deleted.
4. Random parens.
5. Explicit default parameters.
6. Unnecessary requires: If nothing uses active support, then don't import it.
7. Stringifying strings that are strings already.
8. Duplicated tests. Except if behavior is needed.
9. A combination of different smells

## Therapy
I vaguely recall writing that code. When I panic I write awful code. I love refactoring. If you have better working memory, you are able to remove things in your brain that you didn't want. So refactoring makes you happier. So you get faster classes for things. Fast tests are awesome. It's a huge enabler for flow.

Happiness leads to good design. "Can this be a separate class?" "Do I need a gem?" You optimize for developer happiness by making your tests really fast.


