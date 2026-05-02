---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
redirect_from:
  - /pubs
---

{% include base_path %}

<div id="pubmed-feed"><em>Loading publications from PubMed...</em></div>

{% raw %}
<script>
async function loadPubMedData() {
  // Updated search term to PubMed's preferred indexing format
  const authorQuery = 'Palshikar MG[Author]'; 
  const searchUrl = `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=pubmed&term=${authorQuery}&retmode=json&retmax=50`;
  
  try {
    const searchRes = await fetch(searchUrl);
    const searchData = await searchRes.json();
    
    // Check if the API returned any IDs
    if (!searchData.esearchresult || !searchData.esearchresult.idlist || searchData.esearchresult.idlist.length === 0) {
      document.getElementById('pubmed-feed').innerHTML = '<p>No publications found for this author query.</p>';
      return;
    }

    const ids = searchData.esearchresult.idlist.join(',');

    const summaryUrl = `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esummary.fcgi?db=pubmed&id=${ids}&retmode=json`;
    const summaryRes = await fetch(summaryUrl);
    const summaryData = await summaryRes.json();

    let html = '<ul style="list-style-type: none; padding-left: 0;">';
    for (const id of searchData.esearchresult.idlist) {
      const paper = summaryData.result[id];
      const authors = paper.authors.map(a => a.name).join(', ');
      const year = paper.pubdate.split(' ')[0];
      const title = paper.title;
      const journal = paper.source;
      const url = `https://pubmed.ncbi.nlm.nih.gov/${id}/`;

      html += `
        <li style="margin-bottom: 20px; padding-bottom: 15px; border-bottom: 1px solid #e6f1f0;">
          <h3 style="margin-top: 0; margin-bottom: 5px;"><a href="${url}" target="_blank" style="text-decoration: none;">${title}</a></h3>
          <p style="margin: 0; font-size: 0.9em; color: #3e6f06;">${authors}</p>
          <p style="margin: 0; font-size: 0.9em;"><em>${journal}</em> (${year})</p>
        </li>`;
    }
    html += '</ul>';
    
    document.getElementById('pubmed-feed').innerHTML = html;
  } catch (error) {
    document.getElementById('pubmed-feed').innerHTML = `<p style="color: red;">Error loading publications: ${error.message}</p>`;
    console.error('PubMed Fetch Error:', error);
  }
}

loadPubMedData();
</script>
{% endraw %}
