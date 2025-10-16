---
layout: page
title: Data Exploration
permalink: /dataexploration/
---

#### **Source**
<p>
<div style="text-align: justify">  
Our dataset comes from the <i>Air Quality Measures on the National Environmental Health Tracking Network</i>, a publicly available resource provided by the <a href='https://catalog.data.gov/dataset/air-quality-measures-on-the-national-environmental-health-tracking-network'>CDC and EPA</a>. It contains nationwide measurements of key air pollutants, including PM2.5, PM10, and ozone levels, collected from approximately 4000 monitoring stations and satellites over multiple years that are managed by the EPA. These collection sites are most commonly in urban areas where air pollutants are at naturally higher levels, which is important to consider as we further investigate the relationship between human activity and pollutant levels.
</div>
</p>


#### **Why This Data?**
<p>
<div style="text-align: justify">  
We selected this dataset because it contains high-quality, standard, and readily available air quality data at both the state and national levels. One of the key components of our analysis was to consider both the local and higher levels so that patterns at both levels could be identified, therefore finding a dataset that would allow for this flexible analysis was key. The coverage and size of the data allowed us to further explore patterns in recent history across various regions in order to identify correlations between pollution and human activity. The essence of our research questions surround this relationship and this dataset allowed us to adequtely several factors that lie at the heart of the issue. Furthermore, being that this is a government managed and updated dataset, there was a high amount of trust that we could place in the integrity of the data and the standards that were used to collect the data. Down the road, this helped minimize the amount of preprocessing that we would have to do to prepare our data for analysis. 
</div>
</p>

#### **Before and After**
<div style="display: flex; justify-content: center; gap: 40px;">

  <div style="text-align: center; width: 500px;">
    <p><strong>Before</strong></p>
    <img src="/image/before.png" alt="Before" width="500">
  </div>

  <div style="text-align: center; width: 500px;">
    <p><strong>After</strong></p>
    <div style="display: flex; justify-content: center; gap: 10px;">
      <img src="/image/after.png" alt="After 1" width="250">
      <img src="/image/after2.png" alt="After 2" width="250">
    </div>
  </div>

</div>

<div style="max-width: 700px; margin: 20px auto; padding: 10px 15px; border: 1px solid #ccc; border-radius: 8px; background-color: #f9f9f9;">
  <p style="font-size: 14px; color: #333;">
    By breaking out and aggregating the original dataset on the 'MeasureName' feature, we were able to create a collection of separated_value datasets which just contain one measurement name and type. This allows for a more streamlined and simplified approach to analyzing specific subgroups of the data that we're interested in.
  </p>
</div>



