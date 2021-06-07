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
- The only two options to maintain at most 3 enemies (races, workload, efficiency
  - Terran - Pirates - Yaki, 162.4439368085864, 0.07387163987622411
  - Terran - Yaki - Paranid, 195.74987462921922, 0.06130272125450844
- 4 options to keep good relationship with all 6 major races with least enemies are listed as below
  - Yaki - Arteus - Pirates - Strong Arms - Duke's, 115.8094676469517, 0.08634872608589542
  - Yaki - Pirates - Strong Arms - Duke's - OTAS, 55.18972548571192, 0.18119314622409025
  - Yaki - Arteus - Pirates - Duke's - OTAS, 59.13128817880327, 0.16911520631449206
  - Yaki - Arteus - TerraCorp - Pirates - Duke's, 280.2498134147293, 0.035682450161711406
