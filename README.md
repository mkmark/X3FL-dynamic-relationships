# X3FL dynamic relationships

Originally posted on [forum.egosoft.com](https://forum.egosoft.com/viewtopic.php?f=199&t=439741&p=5061950)

The interactive tool is located at 

[X3FL-dynamic-relationships-tool.ipynb](https://colab.research.google.com/github/mkmark/X3FL-dynamic-relationships/blob/main/X3FL-dynamic-relationships-tool.ipynb)

Moreover, an interactive analysis report is located at

[X3FL-dynamic-relationships.ipynb](https://colab.research.google.com/github/mkmark/X3FL-dynamic-relationships/blob/main/X3FL-dynamic-relationships.ipynb)

---

**This is NOT JUST a dynamic relationships stability checking tool. It gives you optimized strategy to achieve specific relationship,** as well as its workload and efficiency.

For example, if you are to become friends with everyone but Yaki, Pirates, and Terran, the best strategy is to improve relationship with everyone but not Yaki, Pirates, Terran, **AND TELADI**, which is quite contrary to intuition. 

The logic behind this strategy is that by improving the relationship with Teladi's ally, it would already make notoriety points of more than enough to achieve good relationship with Teladi, which is verified by the tool.

---

This is a feature not planned but discovered during the analysis. Instead of [blazenclaw's strategy](https://github.com/dzfischer/X3FL-DRCalculation/tree/master) to recursively improving relationship with the race of worst relationship, this tool generates solutions in a more mathematical way that allows the strategy to be optimized.

---

I was really intrigued by the new dynamic relation system but could not find a source telling me what is actually happening behind all the notoriety shift, so when I found [blazenclaw's work](https://forum.egosoft.com/viewtopic.php?f=199&t=438936=) I was very excited.

blazenclaw has done a lot in researching the dynamic relationship, and gave several lists of enemy combo to choose from(see his [latest progress here](https://steamcommunity.com/sharedfiles/filedetails/?id=2499635590)). I was not aware of what approach he was using at then this but I wanted to explore the problem myself so I write a tool to address this.

The result is slightly different from [blazenclaw's work](https://github.com/dzfischer/X3FL-DRCalculation/tree/master). Long story short,
- A simple tool is developed that allows to generate best strategy to achieve desired relationships
- All 283 possible combos are given with total workload and efficiency
- The only two options to maintain at most 3 enemies (races, workload, efficiency)
    - Terran - Yaki - Paranid, 195.74987462921916, 0.06130272125450846
    - Pirates - Terran - Yaki, 162.4439368085863, 0.07387163987622415
- 4 options to keep good relationship with all 6 major races with least enemies (5) are listed as below:
    - Atreus - Pirates - Duke's - Strong Arms - Yaki, 115.80946764695183, 0.08634872608589532
    - OTAS - Pirates - Duke's - Strong Arms - Yaki, 55.18972548571193, 0.18119314622409022
    - Atreus - TerraCorp - Pirates - Duke's - Yaki, 280.2498134147285, 0.03568245016171151
    - OTAS - Atreus - Pirates - Duke's - Yaki, 59.131288178803246, 0.16911520631449212

---

Credits to blazenclaw, Deianeira from [forum.egosoft.com](https://forum.egosoft.com/viewtopic.php?f=199&t=439741&p=5061950#p5061950)