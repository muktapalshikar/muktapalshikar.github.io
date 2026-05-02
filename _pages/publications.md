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

<script>
async function loadPubMedData() {
  var authorQuery = 'Palshikar MG[Author]'; 
  var searchUrl = 'https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=pubmed&term=' + authorQuery + '&retmode=json&retmax=50';
  
  try {
    var searchRes = await fetch(searchUrl);
    var searchData = await searchRes.json();
    
    if (!searchData.esearchresult || !searchData.esearchresult.idlist || searchData.esearchresult.idlist.length === 0) {
      document.getElementById('pubmed-feed').innerHTML = '<p>No publications found for this author query.</p>';
      return;
    }

    var ids = searchData.esearchresult.idlist.join(',');
    var summaryUrl = 'https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esummary.fcgi?db=pubmed&id=' + ids + '&retmode=json';

    var summaryRes = await fetch(summaryUrl);
    var summaryData = await summaryRes.json();

    var html = '<ul style="list-style-type: none; padding-left: 0;">';
    
    for (var i = 0; i < searchData.esearchresult.idlist.length; i++) {
      var id = searchData.esearchresult.idlist[i];
      var paper = summaryData.result[id];
      
      var authorsArray = [];
      if (paper.authors && paper.authors.length > 0) {
        for (var j = 0; j < paper.authors.length; j++) {
          authorsArray.push(paper.authors[j].name);
        }
      }
      var authors = authorsArray.join(', ');
      
      var year = paper.pubdate ? paper.pubdate.split(' ')[0] : '';
      var title = paper.title;
      var journal = paper.source;
      var url = 'https://pubmed.ncbi.nlm.nih.gov/' + id + '/';

      html += '<li style="margin-bottom: 20px; padding-bottom: 15px; border-bottom: 1px solid #e6f1f0;">';
      html += '<h3 style="margin-top: 0; margin-bottom: 5px;"><a href="' + url + '" target="_blank" style="text-decoration: none;">' + title + '</a></h3>';
      html += '<p style="margin: 0; font-size: 0.9em; color: #3e6f06;">' + authors + '</p>';
      html += '<p style="margin: 0; font-size: 0.9em;"><em>' + journal + '</em> (' + year + ')</p>';
      html += '</li>';
    }
    
    html += '</ul>';
    document.getElementById('pubmed-feed').innerHTML = html;
    
  } catch (error) {
    document.getElementById('pubmed-feed').innerHTML = '<p style="color: red;">Error loading publications: ' + error.message + '</p>';
    console.error('PubMed Fetch Error:', error);
  }
}

loadPubMedData();
</script>
