---
filename: "Copy of mcp-466-cswg-workshop-push-notifications-and-git-branching"
revision:
  id: 1
  last revised: "2026-03-11T19:57:07.447Z"
  modified_by: "JJ Salley"
  email: "jjsalley@gmail.com"
---


---

<span style="font-size:10PT"><b>Name: </b></span><span style="font-size:10PT">mcp-466-cswg-workshop-push-notifications-and-git-branching</span>


<span style="font-size:10PT"><b>Title: </b></span><span style="font-size:10PT">Push notifications and Git branching</span>


<span style="font-size:10PT"><b>Status</b></span><span style="font-size:10PT">: Draft -- anyone can edit. </span>


_See the _<a href="http://mcp.systems"><span style="color:#1155cc"><u><i>MCP index</i></u></span></a>_ to create or find documents, or _<a href="http://bit.ly/nom-mcp"><span style="color:#1155cc"><u><i>mcp-0-readme</i></u></span></a>_ for an overview.  _


_The headers above are machine-readable; please preserve format._


Text checkins


- Steve
  - passed stage 1 check oral exam
    - flight portion next Tuesday, (re)solo Wednesday or Friday next week
    - spent last weekend studying, will need to spend this weekend simming
  - Cat surgery and furnace repairs yesterday
  - Now resumed work on timeline items 
    - decomk
    - mob-consensus
    - grokker/storm refactor
-  JJ
  - Going to Bsides infosec conference on Fri and Sat.…. I gave llm lots of team readmes, asked it to find the perfect schedule, it even listed what project it would benefit: <a href="https://drive.google.com/file/d/1azEsITQOf-v3i40T08VwtKX-kD6Z3TCf/view?usp=sharing"><span style="color:#1155cc"><u>https://drive.google.com/file/d/1azEsITQOf-v3i40T08VwtKX-kD6Z3TCf/view?usp=sharing</u></span></a>  
  - Looked into push notifications
  - Codespace for collab editor stuff.  I was able to see the same doc from another computer using a codespace earlier this week: <a href="https://github.com/ciwg/collab-codespace"><span style="color:#1155cc"><u>https://github.com/ciwg/collab-codespace</u></span></a>  the collab-codespace tab from my shared doc on the side has photos!!
  - Dog problems
  - Lots of driving with my 21 year old
  - A talk from the Santa Fe Institute, with a professor from UC Davis: [Giving Groups Control Over the Rules of the Game, in Simulation, in the Lab, and in the Wild](https://www.youtube.com/watch?v=087fB2jZesc&fbclid=IwY2xjawQN1lhleHRuA2FlbQIxMABicmlkETFoNGtkbDhqbmdBRHUybEIzc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHrkXZ7T5M0XldjtOA81io0K8uVUrnQjeEMDPtNRRKvKlMXSWRCy1b-CuDtOn_aem_U59Et9HQ6rFMv_i4-J4JPA)	
- Richard
  - Flying back from desert on Saturday. The wild flowers are starting to show up. My cactus garden is looking good
  - Open Edx is now pretty stable and have been playing around remotely quite a bit. I asked some AI if Open Edx was in use by Fab Labs or Maker Spaces. I’d have to remind myself but basically it said well yes of course its a natural but couldn’t find any examples. Fab Foundation didn’t seem to have any specific info. Is there a fab lab or maker space out there somewhere using Open Edx?
  - The main url I have is learn.soupstone.zone and you should be able to set up an account and either get an email or just hit the accept button. There is a standard Edx demo and one I’m experimenting with. 
  - There’s an Edx annual conference in Salt Lake City in May I think. I might go
  - This platform, in time, could be a good way to put up explanatory/tutorial stuff about Promise Grid. Think of it as powerpoint on steroids.
- Donaldo
  - I cancelled wifi, may have interruption March 9, but have library & makerspace as an option
  - Catching up on microelectronics course; coming up with ideas for my design, maybe a <a href="https://en.wikipedia.org/wiki/Cellular_automaton"><span style="color:#1155cc"><u>cellular automaton </u></span></a>or neuron
  - TXRX is doing a Cable & Harness Assembly training from April 13-May 14
    - IPC/WHMA-A-620 certification
      - <a href="http://whma.org"><span style="color:#1155cc"><u>whma.org</u></span></a> - Wire Harness Manufacturing Association
    - One more class I didn't expect 😩 but i signed up for a seat
- Rebecca
  - Back in Albuquerque
    - This trip went pretty well and things are at a good place
    - Parents have shown a lot of interest in moving to a retirement apartment, I'd probably be dealing with a lot around a house sale if they do this, but on the whole I would expect it would be a situation that would meet their future needs much better
  - Had a very stressful thing happen last night (I don't mind talking about it but don't feel like writing it down), it didn't affect anyone I know, and I am feeling a lot better, but might still be a bit distracted by it

Timeline


- <a href="https://gitea.t7a.org/cswg/coordination/src/branch/main/timeline.md"><span style="color:#1155cc"><u>https://gitea.t7a.org/cswg/coordination/src/branch/main/timeline.md</u></span></a> 
  - Mob consensus going really well
  - storm/grokker refactor is behind
  - Discussion of plan mode in Codex, good for short term where you don't need a long term to-do or checklist
  - Grokker being cloned, rather than renamed, to preserve dependencies

Push notifications and Git branching 


- Core problem:  In a world with LLMs editing 100X the volume of code, git merge conflicts are unmanageable by humans
  - longer term, LLMS themselves will help with merging, or deconflicting
  - in the short term, we need to manually communicate pretty verbosely to head off merge conflicts before they happen
- Practice repo, not the repo for today's demo, but it has lots of other stuff: <a href="https://github.com/computerscienceiscool/git-practice-repo.git"><span style="color:#1155cc"><u>https://github.com/computerscienceiscool/git-practice-repo.git</u></span></a>
- Ntfy page: <a href="https://ntfy.sh/nfty-test-jj-2026"><span style="color:#1155cc"><u>https://ntfy.sh/nfty-test-jj-2026</u></span></a>
  - *sidenote: its 'TF' not 'FT'
  - Ntfy's pricing page is nicely worded, friendly in transparency, developer, affordability. <a href="https://ntfy.sh/#pricing"><span style="color:#1155cc"><u>https://ntfy.sh/#pricing</u></span></a> 
    - Compare to Twilio, no prices listed, a ton of different plans, not open
    - Twilio also requires a lot of different things around how data is stored, opting in, we would need a compliance person to track this
- <span style="color:#188037"><span style="font-family:'Roboto Mono'">git log --all --graph</span></span>
  - display commits and messages, row by row
- <span style="color:#188037"><span style="font-family:'Roboto Mono'">git log --oneline --all --graph</span></span>
  - shows the merges as a graph
- <span style="color:#188037"><span style="font-family:'Roboto Mono'">git mergetool</span></span>
  - Mob-consensus helps with this, pops-up difftool, executes the merge, displays the merge
- mob-consensus does this, in this order:
  - git difftool {local branch} {remote branch}  
    - shows differences between local and remote branches
  - git merge {remote branch}
    - merges remote changes into local branch, potentially creating merge conflicts
  - git mergetool   
    - helps with resolving merge conflicts
- Next implementing LLM based merge conflict resolution
  - more advanced mob-consensus features
- Other applications of ntfy 
  - Makerspace, equipment is down, print is done, machine is busy
  - Maintence
- "Wait, doesn't Github already have a mobile app?"
  - What we're getting at is NOT only when a merge or commit is create, but ALSO when someone is working on a branch, in a repo hacking on stuff
    - LLM could eventually say something like "Hey Steve is working on this, seems like it might conflict with what you've started working on [...]"
  - You can extend to non-Github remotes, ie. Gitea, Gitlab, etc.
  - Github app forces you to work in a particular workflow (for better and for worst)
    - reading review seems to be 'read only' on many things

Post meeting


- Interesting groups
  - Santa Fe Institute <a href="https://www.santafe.edu/"><span style="color:#1155cc"><u>https://www.santafe.edu/</u></span></a>
  - <a href="https://mindbrain.ucdavis.edu/"><span style="color:#1155cc"><u>https://mindbrain.ucdavis.edu/</u></span></a> 
  - <a href="https://www.youtube.com/results?search_query=seth+frey"><span style="color:#1155cc"><u>https://www.youtube.com/results?search_query=seth+frey</u></span></a> 
- Steve uploaded exam book to chatgpt and did a voice chat to simulate oral examiner grilling you about the stuff
  - JJ: Will there be an increase in oral exams due to AI?
    - Instructor would be a bottle neck in grading, but flipped on its head, AI is performing the examination
  - 

