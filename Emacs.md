One example of synergy I have is that of TODO code comments and org-mode agenda scheduling. For context, some programmers leave //TODO comments through their projects. org-mode uses a notation syntax of *TODO to capture and schedule an agenda item for later completion. These agenda items can be scheduled on a calendar and the agenda can be queried for day, week, month TODOS.

Org mode has custom templates for capturing org agenda items. I've made a "TODO code comment" capture template that I can execute on TODO comments. Once executed the template creates org-mode entries which are added to the calendar and link to the comments file and line number.

(https://news.ycombinator.com/vote?id=34589520&how=up&goto=item%3Fid%3D34580943)

[Vekz](https://news.ycombinator.com/user?id=Vekz) [3 months ago](https://news.ycombinator.com/item?id=34589520) | [root](https://news.ycombinator.com/item?id=34580943#34589051) | [parent](https://news.ycombinator.com/item?id=34580943#34589104) | [next](https://news.ycombinator.com/item?id=34580943#34592771) [–]

  

This is what I have, it def could be improved:

```
  (defun capture-comment-line (&optional line)
    (let ((c
          (save-excursion
            (save-window-excursion
              (switch-to-buffer (plist-get org-capture-plist :original-buffer))
            comment-start)
            )))
      (while (string-prefix-p c line)
        (setq line (string-remove-prefix c line)))
      (comment-string-strip line t t)
      ))

  (setq org-capture-templates
        '(("C" "TODO code comment" entry (file+headline "~/org/brain/code.org" "Tasks")
          "\* %(capture-comment-line \"%i\")\n  %a"
          )))
```


This is what I did, years back. I created a single Org-Mode file called tasks.org. I didn't know anything about Org-Mode and in general, was a total noob in Emacs.

Whenever I had a question or felt like whatever I'm doing is taking too long or does require repetition, or simply annoyed me for any reason, I would add a new item to that list.

Slowly I learned Org-Capture, which allowed me to add items to the list much faster and without switching contexts. My list kept growing, and that forced me to learn more efficient ways of finding stuff - e.g., Org-Agenda, scheduling, deadlines, etc.
Some items, over time, have become irrelevant so I learned how to archive them. Some problems required basic knowledge of Emacs-Lisp, so I started using Org-Babel to have source blocks where I would write and play around with tiny (and sometimes bigger) elisp snippets. That lead me to the discovery of indirect buffers and I realized how amazing they are.

That single .org file had become a very important part of my life. I started using it for other things, not just to learn Emacs and Org-Mode. By the time I discovered Org-Roam and jumped into Zettelkasten, I was doing pretty much almost everything I do on the computer, in Emacs. Today I write code, check email, browse articles and blogposts, manage all my files, read books, extract subtitles from videos (to take notes), and keep my personal journal - I do all that in Emacs. And it all started with a simple .org file.
Eventually, this approach become my personal philosophy, my absolute recipe for any problem in my life - If you need to solve something, start with a simple list.
**make baby steps**

https://www.reddit.com/r/orgmode/comments/1316klb/chatgpt_inline_insertion_in_latest_chatgptshell/

Don't overthink it. Develop a habit where you ask yourself a single question every time you make a note - whether it's a scribble on the margins, an org-roam node, a reminder, or any other form of note-taking. Ask yourself, "In what context should I find this in the future?"


**
`C-x k`

kill current buffer without asking

`M-n`

open a new frame

`` M-` ``

switch to other frame

`C-x C-c`

delete the current frame; exit if no frames remain

`C-c r`

interactive select from recent files

`<M-return>`

toggle maximization of current frame
**