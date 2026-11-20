Yes. For Claude Code, you need to use the claude-code branch of the repository, not the default copilot branch. The README explicitly says each AI tool has its own branch, including claude-code.

Setup with Claude Code
Clone the repository:
Shell
git clone https://github.com/i-am-manware/Manware-s-AI-Learning-Toolkit.git

```shell 
cd Manware-s-AI-Learning-Toolkit
```


Switch to the Claude Code branch:

```Shell
git checkout claude-code
```

Or clone it directly:

Shell
git clone -b claude-code https://github.com/i-am-manware/Manware-s-AI-Learning-Toolkit.git

Open the project in the directory where you normally run Claude Code.

Make sure Claude Code can see the toolkit files from the repository. The branch contains the Claude-specific configuration and prompts.

Start Claude Code and use the commands/workflows provided by the toolkit, such as:

/learn
/hint
/debug
/read
/code-review
/test
/explore
/arch
/explain
/retrieve
/api

These prompts are designed to make the AI guide your thinking instead of generating complete solutions immediately.

If Claude Code doesn't recognize the slash commands

Some Claude Code versions don't support custom slash commands exactly like Copilot. In that case, open the prompt files from the toolkit and tell Claude:

"Use the /hint workflow from Manware's AI Learning Toolkit."

or

"Act according to the /debug workflow in this repository."

The behavioral instructions are still useful even if the commands aren't registered as native slash commands.

If you want, I can inspect the claude-code branch and show the exact files Claude Code uses (CLAUDE.md, agents, commands, etc.) and the recommended folder structure.