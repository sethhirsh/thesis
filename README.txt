This directory contains the files necessary to compile
a complete LaTeX thesis in a style suitable for an
Allegheny College senior comp thesis.

***************
CREATED:  Spring 2003
MODIFICATIONS:
   Feb. 19, 2004 -- added new gatorthesis.sty,
          to create the correct Title Page for
          Allegheny tech documents, and updated
          AllegThesis.tex to set the Tech Report Number field.
   Feb. 24, 2004 -- renamed mybibtexDB.bib to myBibtexDB.bib
          as it was called in AllegThesis.tex.  This compiled
          fine on WinXX platforms but broke in Unixland.
   Jun. 15, 2005 -- Added WinEdt .prj file for entire thesis.
          This must be opened from within WinEdt using the "Open Project"
          command from the Project menu.  The "gather" and "tree" commands
          will then create the tree representation for the project, and
          allow pop-up menus for citations and referencing labels.
          
***************
USING THE TEMPLATES
       
The main .tex document is AllegThesis.tex...to compile
the entire document, run

latex AllegThesis
bibtex AllegThesis
latex AllegThesis
latex AllegThesis
...

with the number of compilations necessary to resolve all
cross-indices and references to the bibliography, figures
and table.

Within AllegThesis, you'll find the following:

%\usepackage[debug,draft,single]{gatorthesis} % for student workcopy
\usepackage[debug,draft,double]{gatorthesis} % for student proof doublespace
%\usepackage[single]{gatorthesis} % for student
%\usepackage[bottom,double]{gatorthesis} % for final department copy
%\usepackage[debug,draft,nolists,nofront,single]{gatorthesis} % more options

Simply remove the comment on the one you choose and be sure the
others are commented out.  For proofing copy, the debug version
automatically gives a date for the current draft, and also numbers
in the upper left corner.

Set author, title, thesis number and readers with the following:

\thesistitle{A Very Fine Senior Comprehensive Thesis}
\thesisauthor{Stuart Dent} \thesisadvisor{I.\ M.\ Firstreader}
\thesisnumber{CS04-01}
\thesisreadera{I.\ M.\ Second}
% \thesisreaderb{I.\ B.\ Third} \thesisreaderc{I.\ B.\ Fourth} \thesisreaderd{I.\ B.\ Fifth}

You can set the table-of-content numbering depth (sections/subsections etc.):

\setcounter{tocdepth}{2}

You can also have LaTeX number the subsections and subsubsections as you like:

\setcounter{secnumdepth}{1}
% Number subsubsections as well...
%\setcounter{secnumdepth}{3}

Table of contents and lists of figures and tables are generated automatically,
and then chapter files thischap.tex are included with the \include{thischap}
command.

\tableofcontents
\listoftables
\listoffigures
%\listofabbreviations
\include{glossary}
\include{ch01_overview} % Introductory chapter

Appendices are included as above, but follow the \appendix command which
switching to lettering chapters rather than numbering them:

\appendix
\include{appa}              % Appendix A---Limit Positions for Thall surfaces
\include{appb}              % Appendix B---Inverting Limit Positions for Meshes

The \nocite command can be used to force Bibtex references for papers
even without citing them in the text.  \nocite{*} includes ALL references
from the Bibtex databases.  This can be used for proofing and creating
a bibliography of your reading list, but a final document should generally
only include cited references:

%\nocite{ckm-acmap-99}		% this includes ckm-acap-99 ref. in bibiography
%\nocite{Dierckx93}
%\nocite{obs-stcav-92}
%\nocite{bb4471}
\nocite{*}						% this includes ALL references--comment out for
                           % final document
