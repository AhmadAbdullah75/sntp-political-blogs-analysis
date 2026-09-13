# SNTP Assignment 1 - Progress Tracker

## Objective
Analyze the Political Blogs Network (polblogs.gml) using graph centrality measures
and community detection to investigate whether hyperlink structure recovers known
political orientations (liberal vs conservative), per SE4095 Assignment 1 spec.

## Deliverables
- Jupyter notebook (notebooks/01_analysis.ipynb) with full implementation
- IEEE-format PDF report (5-7 pages, excluding appendix)
- README with setup + run instructions
- Processed data (if preprocessing changes the graph)
- Final submission: StudentID_SNTP_Assignment.zip

## Tech Stack
Python 3.12.9, NetworkX, pandas, numpy, matplotlib, scipy, python-louvain,
scikit-learn, Jupyter

## Project Structure

./
.gitignore
progress.md
README.md
requirements.txt
data/
processed/
analysis_graph.graphml
targeted_graph.graphml
random_graph.graphml
raw/
polblogs.gml
notebooks/
01_analysis.ipynb
reports/
figures/
community_size_distribution.png
community_visualization.png
degree_distribution.png
network_visualization.png

```

## Completed Steps
- [x] Step 0: Verified Python installed, downloaded polblogs.gml
- [x] Step 1: Project scaffolding, venv, dependencies, notebook skeleton created
- [x] Part A: Load, clean, describe graph. Original nodes: 1490, edges: 19090. Collapsed duplicate edges: 65. Self-loops removed: 3. Nodes missing 'value' attribute: 0. Isolates removed: 266. Weakly connected components: 2. Strongly connected components: 422. Final analysis_graph size: 1222 nodes, 19021 edges. **Processed export**: analysis_graph saved to data/processed/analysis_graph.graphml (920.6 KB).
- [x] Part B: Centrality selection and ranking. Top-3 PageRank: dailykos.com (0.0189), atrios.blogspot.com (0.0160), instapundit.com (0.0133). Top-3 Betweenness: blogsforbush.com (0.1467), atrios.blogspot.com (0.0611), instapundit.com (0.0512). Spearman correlation: 0.758. Top-10 overlap count: 5.
- [x] Part C: Centrality-informed removal experiment. Removed exactly 61 nodes (5%). Targeted removed: dailykos.com, atrios.blogspot.com, instapundit.com, blogsforbush.com, talkingpointsmemo.com, michellemalkin.com, drudgereport.com, washingtonmonthly.com, powerlineblog.com, andrewsullivan.com, juancole.com, littlegreenfootballs.com/weblog, vodkapundit.com, rightwingnews.com, volokh.com, nationalreview.com/thecorner, hughhewitt.com, truthlaidbear.com, prospect.org/weblog, freerepublic.com, digbysblog.blogspot.com, talkleft.com, yglesias.typepad.com/matthew, jameswolcott.com, jewishworldreview.com, politicalwire.com, kausfiles.com, j-bradford-delong.net/movable_type, wizbangblog.com, realclearpolitics.com, captainsquartersblog.com/mt, lashawnbarber.com, wonkette.com, rogerlsimon.com, pandagon.net, right-thinking.com, mydd.com, moorewatch.com, democraticunderground.com, reachm.com/amstreet, outsidethebeltway.com, iraqthemodel.blogspot.com, stevegilliard.blogspot.com, crookedtimber.org, emergingdemocraticmajorityweblog.com/donkeyrising, gadflyer.com, scrappleface.com, belmontclub.blogspot.com, lucianne.com, billmon.org, maxspeak.org/mt, thismodernworld.com, tbogg.blogspot.com, oliverwillis.com, timblair.net, asmallvictory.net, etalkinghead.com, liberaloasis.com, americablog.blogspot.com, gevkaffeegal.typepad.com/the_alliance, riverbendblog.blogspot.com. Random removed (seed 42): islanddave.blogspot.com, bakshi.us/redskunk, wampum.wabanaki.net, tesibria.typepad.com/democracy_is_coming, scottcsmith.net, lightupthedarkness.org, homepage.mac.com/elisa_camahort/iblog, stmonk.blogspot.com, farleft.blogspot.com, winceandnod.blogspot.com, jrogg.blogspot.com, blog.kenlan.net, blog.dccc.org, goose3five.blogspot.com, rowhouselogic.com, soonerthought.com, rednyc.blogspot.com, battleground-wisconsin.blogspot.com, thepatriette.com, pollsterseek.blogspot.com, joshferguson.blogspot.com, s88172659.onlinehome.us/spockosbrain.html, mhking.mu.nu, wholewheatblogger.com, whopundit.blogspot.com, alicublog.blogspot.com, michaelberube.com, juntoboys.blogspot.com, cdharris.net, mcwil.blogspot.com, rittenhouse.blogspot.com, calirep.blogspot.com, gisleson.com/blog, emilythedog.blogspot.com, hal9000report.blogdrive.com, d-42.com, chiefsblog.blogspot.com, tomherod.blogspot.com, bowles2004.com/weblog, mypetjawa.mu.nu, slowplay.com, justmark.com, electionprojection.com, eastbaykerry.com, tepid-observer.blogspot.com, alexpelan.blogspot.com, daisycutter.blogspot.com, tuckereskew.typepad.com, phillybri.blogspot.com, dems2000.net, browncross.com/usualsuspects, shininglight.us, achicknamedmarzi.com, elderbearden.blogspot.com, home.earthlink.net/~fsrhine, mostlycajun.com, deanesmay.com, mixtersmix.blogspot.com, discerningtexan.blogspot.com, conservativezone.blogspot.com, realitybasednation.com. Original graph (1222 nodes, 19021 edges, largest comp 1222); Targeted graph (1161 nodes, 10279 edges, largest comp 1071); Random graph (1161 nodes, 17404 edges, largest comp 1155). **Processed exports**: targeted_graph saved to data/processed/targeted_graph.graphml (573.2 KB); random_graph saved to data/processed/random_graph.graphml (849.3 KB).
- [x] Part D: Community detection (Louvain, 5 seeds). Original: ~10.8 communities, 0.4269 modularity, top comm size 635 (94.8% purity). Targeted: ~101.2 communities, 0.4583 modularity. Random: ~14.0 communities, 0.4239 modularity.
  - Added full community size distribution (all communities, not just top 5): Original 11 communities sizes=[635,526,40,4,4,3,2,2,2,2,2]; Targeted 100 communities (97 singletons after 3 large ones); Random 14 communities sizes=[602,493,39,4,4,3,3,3,2,2,2,2,1,1]. Figure saved to reports/figures/community_size_distribution.png.
- [x] Part E: Pairwise community evaluation (vectorized numpy, <0.1s per graph). Original: Acc=0.8835, Prec=0.9210, Rec=0.8392, F1=0.8782 (TP=313296 TN=345822 FP=26874 FN=60039). Targeted: Acc=0.7464, Prec=0.9094, Rec=0.5478, F1=0.6837 (TP=184576 TN=318030 FP=18398 FN=152376). Random: Acc=0.8804, Prec=0.9237, Rec=0.8297, F1=0.8742 (TP=279840 TN=313005 FP=23105 FN=57430). Modularity vs F1: Original 0.4269/0.8782, Targeted 0.4583/0.6837, Random 0.4239/0.8742.
- [x] Part F: Reproducibility verified. Seed audit passed (all seeds reference RANDOM_SEED=42 or SEEDS=[42,43,44,45,46], no bare integers). Added Part F Conclusion and Limitations markdown cell with actual result numbers. Full clean kernel-restart re-run completed with zero errors. README.md created with setup instructions, project structure, and seed documentation.

## Errors & Solutions
- **NetworkXError on polblogs.gml**: `nx.read_gml()` failed because of duplicate edges. Fixed by inserting `multigraph 1` into the GML file header, loading it as a MultiDiGraph, and dropping duplicates to create a simple DiGraph.
- **PowerShell script error**: During setup, PowerShell `$_` context was lost causing `tree` script error. Resolved by using a custom Python `os.walk` script.

## Current Status
Notebook fully implemented (Parts A-F). Full clean kernel-restart verification re-run completed successfully (zero errors) with all three processed graph exports in place:
- data/processed/analysis_graph.graphml (920.6 KB) — exported after Part A Final Graph Summary
- data/processed/targeted_graph.graphml (573.2 KB) — exported after Part C removal experiment
- data/processed/random_graph.graphml (849.3 KB) — exported after Part C removal experiment
README.md created.
Remaining: fill interpretation cells manually, write IEEE-format report (manual), and create final submission zip (StudentID_SNTP_Assignment.zip).

## Remaining Tasks
- Write IEEE-format PDF report (manual, outside coding agent)
- Create final submission zip: StudentID_SNTP_Assignment.zip
