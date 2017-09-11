# Humanlights.Twitter
A console application of hooking git commits and sending them to Twitter.

## Usage
The application is best used with git hooks, it is only created for printing commits, not posting random tweets on Twitter.
It uses one of my personal projects which I use as extension apps for Jenkins (for instance) which is **Humanlights.GitBatch**, which gets the commit informations from a repository folder that usually is called ".git" and stores a json file of it.

### Humanlights.GitBatch
In order to make Humanlights.Twitter work, you'll have to input a json file that is generated by GitBatch. 
Since both apps are console applications and use command-lines (ran through .bat or .sh files), here is a sample of how to use GitBatch.
<p><code>Humanlights.GitBatch.exe -git ".git" -json "git_commit.json"</code></p>

- <code>-git</code>: The git folder.
- <code>-json</code>: Where the json file will be exported.
- <code>-keepTemp</code>: (Optional) Does not remove the files generated thoughout the process.

### Humanlights.Twitter
This application uses lots of dll assembly dependencies/references because of the main plugin it uses, **Tweetinvi** (NuGet) to post stuff to Twitter.
<p><code>Humanlights.Twitter.exe -credentials "credentials.json" -commit "git_commit.json" +repo "Humanlights.Twitter"</code></p>
<p><code>Humanlights.Twitter.exe -credentials "credentials.json" -commit "git_commit.json" +repo "Humanlights.Twitter" +tweetFormat "[message][RETURN][RETURN][author_name] on [branch]#[changeset]" +replyFormat "Changes: [changes_long]" +reply</code></p>

- <code>-credentials</code>: Credentials json file. You have to make a Twitter application and get consumer key, consumer secret, user access token and user access secret.
- <code>-commit</code>: Path to commit file generated by Humanlights.GitBatch.
- <code>+repo</code>: (Optional) It is basically repository name which is right next to branch, in format of [repositoryName][branch]#[changeset].
- <code>+tweetFormat</code>: (Optional) The twitter message format. "[message][RETURN][RETURN][author_name] on [branch]#[changeset]" by default. Which every single [] case is being replaced.
- <code>+replyFormat</code>: (Optional) The twitter message format. "[changes_long]" by default.
- <code>+reply</code>: (Optional) Enable posting commit reply. (Only posts attached to the first commit, if multiple lined) Be aware that if using +replyFormat, this needs to be added as well to work.

## License
See [license][License] (hint: MIT).

[License]: https://github.com/Humanlights/Humanlights.Twitter/blob/master/LICENSE
