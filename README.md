# X3FL dynamic relationships

Originally posted on [forum.egosoft.com](https://forum.egosoft.com/viewtopic.php?f=199&t=439741&p=5061950#p5061950)

I was really intrigued by the new dynamic relation system but could not find a source telling me what is actually happening behind all the notoriety shift, so when I found [blazenclaw's work](https://forum.egosoft.com/viewtopic.php?f=199&t=438936=) I was very excited.

blazenclaw has done a lot in researching the dynamic relationship, and gave 2 lists of enemy combo to choose from(see his [latest progress here](https://steamcommunity.com/sharedfiles/filedetails/?id=2499635590)). I was not aware of what approach he was using at then this but I wanted to explore the problem myself so I write a tool to address this.

[X3FL-dynamic-relationships-tool.ipynb](https://colab.research.google.com/github/mkmark/X3FL-dynamic-relationships/blob/main/X3FL-dynamic-relationships-tool.ipynb)

which gives you an output of optimized tactic (which races you should be working on actively) together with its workload and efficiency.

The complete analysis is posted on

[X3FL-dynamic-relationships.ipynb](https://colab.research.google.com/github/mkmark/X3FL-dynamic-relationships/blob/main/X3FL-dynamic-relationships.ipynb)

The result is different from blazenclaw's work. Long story short,
- A simple tool is developed
- All 283 possible combos are given with total workload and efficiency
- The only two options to maintain at most 3 enemies (races, workload, efficiency)
    - Terran - Yaki - Paranid, 195.74987462921916, 0.06130272125450846
    - Pirates - Terran - Yaki, 162.4439368085863, 0.07387163987622415
- 4 options to keep good relationship with all 6 major races with least enemies (5) are listed as below:
    - Arteus - Pirates - Duke's - Strong Arms - Yaki, 115.80946764695183, 0.08634872608589532
    - OTAS - Pirates - Duke's - Strong Arms - Yaki, 55.18972548571193, 0.18119314622409022
    - Arteus - TerraCorp - Pirates - Duke's - Yaki, 280.2498134147285, 0.03568245016171151
    - OTAS - Arteus - Pirates - Duke's - Yaki, 59.131288178803246, 0.16911520631449212