<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Libtech</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      background-color: #1560BD;
    }

    .header {
      background-color: black;
      color: white;
      padding: 20px;
      font-size: 1in;
      font-weight: bold;
      font-family: 'Times New Roman', serif;
      text-align: center;
      position: relative;
    }

    .auth-container {
      position: absolute;
      top: 10px;
      left: 10px;
      display: flex;
      gap: 10px;
      border: 2px solid white;
      padding: 5px;
      border-radius: 5px;
      background-color: black;
    }

    .auth-container button {
      font-size: 14px;
      font-weight: bold;
      border: none;
      background: white;
      cursor: pointer;
      padding: 5px 10px;
      border-radius: 5px;
    }

    .search-container {
      max-width: 600px;
      margin: 20px auto;
      display: flex;
      align-items: center;
      justify-content: center;
      background: white;
      padding: 10px;
      border-radius: 5px;
    }

    input {
      width: 80%;
      padding: 10px;
      font-size: 16px;
      border: none;
      outline: none;
    }

    button {
      padding: 10px;
      border: none;
      background: none;
      cursor: pointer;
    }

    .results {
      margin-top: 20px;
      text-align: left;
      max-width: 600px;
      margin: auto;
    }

    .paper {
      border: 1px solid #ddd;
      padding: 10px;
      margin: 5px 0;
      background: white;
    }
  </style>
</head>

<body>
  <div class="header">
    <div class="auth-container">
      <button>Sign In</button>
      <button>Log In</button>
    </div>
    Libtech
  </div>
  <div class="search-container">
    <input type="text" id="searchInput" placeholder="Search" onkeypress="handleKeyPress(event)">
    <button onclick="searchTechnology()">
      <img src="https://cdn-icons-png.flaticon.com/512/622/622669.png" alt="Search" width="20" height="20">
    </button>
  </div>
  <div class="results" id="results"></div>

  <script>
    const researchPapers = [{
        title: "Technology as experience",
        author: "John McCarthy",
        link: "https://dl.acm.org/doi/abs/10.1145/1015530.1015549"
      },
      {
        title: "Waterjetting Technology",
        author: "D.A. Summers",
        link: "https://www.taylorfrancis.com/books/mono/10.1201/9781482294828/waterjetting-technology-summers"
      },
      {
        title: "Are Technology Improvements Contractionary?",
        author: "Susanto Basu",
        link: "https://www.aeaweb.org/articles?id=10.1257/aer.96.5.1418"
      },
      {
        title: "Technology as Knowledge",
        author: "Edwin T. Layton Jr.",
        link: "https://muse.jhu.edu/pub/1/article/892822/summary"
      },
      {
        title: "Technology is society made durable",
        author: "Bruno Latour",
        link: "https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1467-954X.1990.tb03350.x"
      },
      {
        title: "How is technology made?",
        author: "Wiebe E. Bijker",
        link: "https://academic.oup.com/cje/article/34/1/63/1702334"
      },
      {
        title: "Technology and trade",
        author: "Gene M. Grossman",
        link: "https://www.sciencedirect.com/science/article/abs/pii/S157344040580005X"
      },
      {
        title: "Technology in Services",
        author: "James Brian Quinn",
        link: "https://www.jstor.org/stable/24979579"
      },
      {
        title: "The 3-D Interconnect Technology Landscape",
        author: "Eric Beyne",
        link: "https://ieeexplore.ieee.org/abstract/document/7438817"
      },
      {
        title: "Emerging hydrovoltaic technology",
        author: "Zhuhua Zhang",
        link: "https://www.nature.com/articles/s41565-018-0228-6"
      },
      {
        title: "A Randomized Trial of Intraarterial Treatment for Acute Ischemic Stroke",
        author: "Olvert A. Berkhemer",
        link: "https://www.nejm.org/doi/full/10.1056/NEJMoa1411587"
      },
      {
        title: "WHO Declares COVID-19 a Pandemic",
        author: "Domenico Cucinotta",
        link: "https://pmc.ncbi.nlm.nih.gov/articles/PMC7569573/"
      },
      {
        title: "The Theory of the Business",
        author: "Peter Drucker",
        link: "https://rlaexp.com/studio/biz/conceptual_resources/authors/peter_drucker/8-the-theory-of-the-business.pdf"
      }
    ];

    function handleKeyPress(event) {
      if (event.key === "Enter") {
        searchTechnology();
      }
    }

    function searchTechnology() {
      const query = document.getElementById("searchInput").value.toLowerCase();
      const resultsContainer = document.getElementById("results");
      resultsContainer.innerHTML = "";
      const filteredPapers = researchPapers.filter(paper =>
        paper.title.toLowerCase().includes(query) ||
        paper.author.toLowerCase().includes(query)
      );
      if (filteredPapers.length === 0) {
        resultsContainer.innerHTML = "<p>No results found.</p>";
      } else {
        filteredPapers.forEach(paper => {
          const paperElement = document.createElement("div");
          paperElement.classList.add("paper");
          paperElement.innerHTML = `<strong>${paper.title}</strong><br>Author: ${paper.author}<br><a href="${paper.link}" target="_blank">Read More</a>`;
          resultsContainer.appendChild(paperElement);
        });
      }
    }
  </script>
</body>

</html>
