# Gov-Search-Html
Gov Search Html 

<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Research GOV TECH</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 text-gray-900 font-sans min-h-screen p-6">

  <div class="max-w-3xl mx-auto">
    <h1 class="text-3xl font-bold mb-6">🔍 Research GOV TECH</h1>

    <!-- Form -->
    <form id="projectForm" class="bg-white p-4 rounded shadow mb-6">
      <h2 class="text-xl font-semibold mb-2">➕ Dodaj projekt GOV</h2>
      <input type="text" id="projectName" placeholder="Nazwa projektu"
             class="w-full mb-2 p-2 border rounded" required>
      <input type="url" id="projectURL" placeholder="https://github.com/..."
             class="w-full mb-2 p-2 border rounded" required>
      <button type="submit"
              class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
        Dodaj projekt
      </button>
    </form>

    <!-- List -->
    <div id="projectList" class="space-y-4">
      <!-- Dynamicznie wstawiane projekty -->
    </div>
  </div>

  <script>
    const form = document.getElementById("projectForm");
    const list = document.getElementById("projectList");

    let projects = [];

    form.addEventListener("submit", e => {
      e.preventDefault();
      const name = document.getElementById("projectName").value.trim();
      const url = document.getElementById("projectURL").value.trim();
      if (!name || !url) return;

      const project = { name, url, archived: false };
      projects.push(project);
      renderProjects();
      form.reset();
    });

    function renderProjects() {
      list.innerHTML = "";
      projects.forEach((p, index) => {
        const item = document.createElement("div");
        item.className = "bg-white p-4 rounded shadow flex justify-between items-center";

        item.innerHTML = `
          <div>
            <a href="${p.url}" target="_blank" class="text-blue-600 font-medium hover:underline">
              ${p.name}
            </a>
            <div class="text-sm text-gray-500">${p.archived ? '📦 Zarchiwzuj
