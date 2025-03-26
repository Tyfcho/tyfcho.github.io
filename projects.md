---
layout: default
title: Projects
---

<h2>GitHub Projects</h2>

<div id="projects-list">
    Loading projects...
</div>

<script>
    fetch("https://api.github.com/users/Tyfcho/repos")
        .then(response => response.json())
        .then(repos => {
            let projectsList = document.getElementById("projects-list");
            projectsList.innerHTML = "";
            repos.forEach(repo => {
                projectsList.innerHTML += `<p><a href="${repo.html_url}" target="_blank">${repo.name}</a> - ${repo.description || ''}</p>`;
            });
        })
        .catch(error => console.error("Error fetching GitHub projects:", error));
</script>
