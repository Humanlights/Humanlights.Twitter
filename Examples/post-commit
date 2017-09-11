#!/bin/sh
"../Humanlights.GitBatch/Humanlights.GitBatch.exe" -git "../.git" -json "git_commit.json"
"../Humanlights.Twitter/Humanlights.Twitter.exe" -credentials "credentials.json" -commit "git_commit.json" +repo "Humanlights.Twitter" +format "[message][RETURN][RETURN][author_name] on [branch]#[changeset]"