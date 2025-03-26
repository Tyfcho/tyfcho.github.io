---
layout: default
title: Projects
---

<h2 class="text-center">Projects</h2>
<div class="row mt-4" id="projects-container">
    Loading projects...
</div>

<script>
    fetch("https://api.github.com/users/Tyfcho/repos")
        .then(response => response.json())
        .then(repos => {
            let container = document.getElementById("projects-container");
            container.innerHTML = "";
            repos.forEach(repo => {
                container.innerHTML += `
                    <div class="col-md-4 mt-3">
                        <div class="card bg-dark border-light shadow-sm">
                            <div class="card-body">
                                <h5 class="card-title">${repo.name}</h5>
                                <p class="card-text">${repo.description || 'No description'}</p>
                                <a href="${repo.html_url}" target="_blank" class="btn btn-outline-light">View Repo</a>
                            </div>
                        </div>
                    </div>`;
            });
        })
        .catch(error => console.error("Error fetching GitHub projects:", error));
</script>
