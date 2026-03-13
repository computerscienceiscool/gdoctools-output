---
revision:
  id: 1
  last revised: "2026-03-11T19:57:23.008Z"
---

**Name:** mcp-465-cswg-workshop-containers-and-codespaces  
**Title:** containers and codespaces  
**Status**: Draft \-- anyone can edit. 

*See the [MCP index](http://mcp.systems) to create or find documents, or [mcp-0-readme](http://bit.ly/nom-mcp) for an overview.*    
*The headers above are machine-readable; please preserve format.*

---

Text checkins

* Steve  
  * cranking on several projects in parallel this week \-- mob-consensus is critical path; also prep for today  
* JJ  
  * Parent’s estate sale started today: [https://www.estatesales.net/NM/Albuquerque/87113/4809606](https://www.estatesales.net/NM/Albuquerque/87113/4809606)    
  * Lots of bio informatics at my house… lots.  Downloaded over 85gb of info from [genomics.com](http://genomics.com)  
  * Middle kid turned 21 yesterday and told me they are dropping out of the mech eng program.  :\\  They plan on doing something with cad and machining… will start machinist training in the fall.  
* Donaldo  
  * First week of microelectronics class  
    * Accidently missed first hour; thought class started on Tue not Mon  
    * Already learning a lot; their setup is pretty cool  
      * Setup containers for everyone  
      * Streamlined accounts creation for Fablab, Gitlab, Mattermost  
  * Chatted with community college on maker education stuff  
    * They also interested in FabLab conference, may collaborate on a workshop regarding gardening & digital fabrication  
  * Listening to podcast JJ & Steve referenced  
  * Finally reached out to Dale to catch up & sort out MakerEd site tidying, maintenance, meeting Monday  
* Rebecca  
  * Will join about an hour late  
* Richard  
  * Finally have an instance of open edx running on the home lab. It just died a few minutes ago after running solid for two days. But its working on public address learn.soupstone.zone though probably offline at the moment. Heading down to the desert on Friday till the 28th.   
  * 

Containers and codespaces 

* Steve: review [https://gitea.t7a.org/cswg/coordination/src/branch/main/timeline.md](https://gitea.t7a.org/cswg/coordination/src/branch/main/timeline.md)  
  * Next Thursday JJ may present on current stuff she's working on, lessons learned  
* (5m) Steve: framing  
  * What we’re trying to learn today: “can we get everyone productive quickly in a container?”  
* (10m) Donaldo: class container playbook \+ short demo inside the class container  
  * VNC \- Virtual Network Computing  
  * A way to access a desktop through browser or VNC client  
  * Issues I've ran into  
    * no VSCode (I guess I'll learn VIM)  
    * the /designs folder is the only persistent folder; everything else gets wiped  
      * they told us we can link it to a git repo to have my own local copy of my assignments  
    * non-editability of lecture pages (even by instructor)  
    * non-obvious fact that you can bring up the class curriculum in a browser in the container  
  * but very performant (runs in AWS)

(30 minute break)

* What are codespaces?  
  * github's implementation of the [containers.dev](http://containers.dev) standard  
    * many implementations, including self-hosted  
  * we'll use them for now, may migrate to DevPod later, eventually grid-hosted \-- more on that below  
* (10m) Steve: demo a codespaces container  
  * log into an existing container and poke around a bit, run:  
    * nvim  
    * mob-consensus  
  * Show how container is defined by .devcontainer/devcontainer.json   
  * Show how tools were installed via .devcontainer/postCreateCommand.sh    
  * Mention the downsides of `postCreateCommand.sh`  
    * it's an ad-hoc devops tool  
    * it will quickly bloat \-- it has no architecture as-is unless you design it  
    * it will be different for each repo's container(s) unless it has even more architecture for detecting which repo's container(s) it's running in, and managing the heterogeneity that requires   
      * e.g. if we had a different `postCreateCommand.sh` in each repo, then we needed to upgrade mob-consensus in each repo's codespaces, then we'd have to touch every stinking `postCreateCommand.sh` in all of our repos  
      * instead, we want one tool sources from one repo, that does the right thing for any container it's cloned into and executed in  
      * the flow we want in a tool is detect container type (based on which repo it's cloned from) ⇒ detect container user ⇒  install the things for that type/user combination  
    * best to use it to call a devops tool  
    * history of [`decomk`](http://github.com/stevegt/decomk) (pronounced "de-co-make")  
  * Show how we're going to call [`decomk`](http://github.com/stevegt/decomk) from `postCreateCommand.sh` instead of bloating postCreateCommand.sh  
* (5m) Roadmap: Codespaces now → self-host later (GCP)  
  * Standardize on the Dev Container spec (`.devcontainer/devcontainer.json`) so repos work in Codespaces now and in self-hosted alternatives later.  
  * Candidate “Codespaces equivalents”: DevPod (client \+ providers) or Coder (self-hosted workspace platform). See TODO 017\.  
  * Longer-term: as Promisegrid stabilizes, host devcontainers on the grid. See TODO 018\.  
  * Optional extension: GUI apps inside devcontainers via VNC/noVNC (Fab Futures example). Track in TODO 019\.  
* (20m) Hands-on: everyone gets into their own copy of the container  
  * Everyone: create a Codespace for `ciwg/mob-sandbox` (choose web UI or `gh`)  
    * Web UI (GitHub.com)  
      * Go to the repo: [`ciwg/mob-sandbox`](https://github.com/ciwg/mob-sandbox)  
      * Click `<> Code` → `Codespaces` → `Create codespace on main (need to use the "+", not the green button)`  
      * Wait for it to finish building; you should land in `/workspaces/mob-sandbox`  
        * `Visible in the terminal window:`  
          * `Welcome to Codespaces! You are on our default image.`   
          *    `- It includes runtimes and tools for Python, Node.js, Docker, and more. See the full list here: https://aka.ms/ghcs-default-image`  
          *    `- Want to use a custom image instead? Learn more here: https://aka.ms/configure-codespace`  
          *   
          * `🔍 To explore VS Code to its fullest, search using the Command Palette (Cmd/Ctrl + Shift + P or F1).`  
          *   
          * `📝 Edit away, run your app as usual, and we'll automatically make it available for you to access.`  
    * GitHub CLI (`gh`) commands  
      * Install `gh` (pick one)  
        * macOS: `brew install gh`  
        * Ubuntu/Debian:   
          * `Copy and paste` this giant blob of commands from this link [https://github.com/cli/cli/blob/trunk/docs/install\_linux.md](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)   
        * Windows: `winget install --id GitHub.cli`  
      * Authenticate: `gh auth login`  
        * `Github.com`  
        * `SSH`  
        * `Generate or skip`  
        * `Use the browser to authenticate`  
      * Create (skip this if you've already created on from the Web UI):   
        * `gh codespace create -R ciwg/mob-sandbox -b main`  
      * List: `gh codespace list`  
        * It will prompt you to run the following:   
        * `gh auth refresh -h github.com -s codespace`  
      * SSH: `gh codespace ssh`  
    * Sanity checks (inside the Codespace): `go version`, `mob-consensus --help`, `codex --help`, `nvim --version`  
  * “Play around” option: run tests, inspect toolchain, try one small edit/commit.  
  * “Do real work” option: make a tiny change and use `mob-consensus` to sync/converge between containers.  
    * Stop:   
      * `gh codespace stop  # this stops billing`  
    * Be sure to type exit or ctrl-d to close out the codespace \-- it will time out 30 minutes later  
* (10m) Wrap-up: capture friction points \+ next steps for the next session  
  * JJ & Steve will troubleshoot tomorrow  
    * Not working on JJ laptop for a problem related to kwallet  
  * Rebecca's needed to run the postCreateCommand  
    * this was in a container started by hitting the big green "open in container" button instead of the plus sign   
    * `Git pull`  
    * `ls .devcontainer/`  
    * `.devcontainer/postCreateCommand.sh`   
  * Rebecca got a transient "too many codespaces" popup  
  * Need to ensure codespaces don't run forever  
    * maybe some sort of monitor that runs using the enterprise API  
  * initial install of the gh command on local non-standard, non-ubuntu or debian machines is likely to always be an adventure  
    * GUI desktop/novnc will sidestep this  
    * pro users can make their own gh environment work


