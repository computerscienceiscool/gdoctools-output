---
revision:
  id: 1
  last revised: "2026-03-11T19:58:39.333Z"
---

**Name:** mcp-463-cswg-workshop-mob-consensus-demo  
**Title:** mob-consensus demo  
**Status**: Draft \-- anyone can edit. 

*See the [MCP index](http://mcp.systems) to create or find documents, or [mcp-0-readme](http://bit.ly/nom-mcp) for an overview.*    
*The headers above are machine-readable; please preserve format.*

---

Text checkins

* Steve  
  * Running late, needs to test some of the code for today  
* Donaldo  
  * Houston Robotics organization setup stalled; I'll continue trying but try not pouring too much effort on it til I can confirm its something we can get done  
  * Using automerge tutorial to pull together my backlog  
    * Doing cleanup of my Obsidian note base to possibly merge in stuff too; beginning to git tracking it   
  * Mentioned storm tool to my startup roundtable, may try a rough demo in the next couple months (rough edges totally okay)  
* JJ  
  * Created first npm package **collab-awareness**\!  This includes awareness code(username, color, cursor).    
  * **vimbeam** \- separate from collab-editor\!  This requires the npm package  
  * Separating editor from **collab-editor**, need good name, right now it is in a package folder on default branch.  
  * So **vimbeam** (with collab-awareness npm package) \+ collab-editor  \= the previous collab-editor  
  * *This is the information BEFORE removing the collab-editor to separate package: [https://github.com/computerscienceiscool/collab-editor-notes/blob/main/awareness.md](https://github.com/computerscienceiscool/collab-editor-notes/blob/main/awareness.md) Gives locations and basic info.*    
  * Really enjoying the Pragmatic Programmer Podcast. Latest episode has Grady Booch as a guest  
* Rebecca  
  * Going to just focus on the presentation instead of thinking about my week at the moment

Plan lineup for following weeks

* Go to workshop schedule & proposals ([mcp-369](https://docs.google.com/document/d/1HPvIs4qEMEZaYHvDpHkg7SXfkgLnm3W-KqAL_oSX9_I/edit?pli=1))

mob-consensus demo 

* repo  
  * [https://github.com/stevegt/mob-consensus](https://github.com/stevegt/mob-consensus)   
* What is this project?   
  * mob-consensus facilitates a different kind of workflow than the typical hub-and-spoke model that platforms like Github are built on  
    * How Github works: In order to collaborate you need to fork a repo, then submit Pull Requests upstream. Requires a central maintainer to facilitate accepting, modifying chances and pushing to the central project  
    * Instead, mob-consensus is a *peer-to-peer*, more easily see each others changes within branches. Collaborate without facilitation of a primary maintainer  
* This is a re-write of a previous 2021 project. Previously in Python, using Codex to Go.  
  * Tests pass\!  
* Steve showing four repos in his temp directory  
  * mc0  
    * Represents a repo hosted on a remote like Github, Gitea, etc.  
  * mc1, mc2, mc3 ("Alice, Bob, Carol")  
    * Represents 3 users  
* Mob consensus uses 'twig' concept  
* Getting started (from the app)  
1. Start from any base, create a shared twig branch  
2. Create your personal branch from that local twig  
3. Push your personal branch  
   1. name your feature branch  
4. Use mob-consensus to converge  
* Alice starts a branch following guide above   
  * Bob pulls Alice branch and switches to it  
    * now Bob does the same guide to create his twig under his copy of Alice's repo  
* (Oops we were using the wrong version of mob-consensus)  
  * Moving it from temp to home directory  
  * Now it works\!  
* what does `mob-consensus` command do? it looks at your branch 'test1' goes through entire tree and shows you if there's any diffs from anyone else's 'test1' branch/twig  
* Now Carol does the same thing  
  * Now when she runs mob-consesus she can also see Alice and Bob content  
* Lets start making edits  
  * At bob mc2  
    * Run `echo hi from bob > README.md`, push changes  
* Now @ Alice, you can see mc2 is ahead  
  * Try `mob-consensus mc2/test1`  
    * It blew up;   
      * Lets try the old code  
        * Also blew up, same error  
  * (For now Steve will manually show rather than debugging in real-time)  
    * The command would bring up a diff view of your branch and the branch you specify  
      * You can then choose to accept changes  
    * Then prompts you for a commit message  
      * We'll probably integrate an LLM for this  
    * Then push (tool does this for you)  
* Switch to carol perspective  
  * Alice ahead 2 changes  
  * Bob ahead 1 change  
* Clue would be to go to Alice branch first since that has most changes  
  * Most changes not always the most recent  
    * Maybe we add '5 minutes ago' , ' 2 days ago', etc.  
    * LLM could even be used to do deeper analysis for more complex merge conflicts  
* Carol does the same and runs a diff and accepts Alice's changes  
*  GENERAL FLOW (when the bugs are fixed)  
  * `mob-consensus`  
    * shows the list of who's ahead and behind  
    * we pick someone who's ahead, e.g. alice/sometwig  
  * `mob-consensus alice/sometwig`  
    * this brings up a diff display, if any files are different  
      * user edits the diff as needed  
    * tool automatically commits and pushes  
* mc0 for now is a centralized remote like Github. In future would be the decentralized infrastructure 'thing' that people would use to sync between  
* q:   
  * The term twig just means 'this part of the branch name', 'the branch suffix', etc.

  
