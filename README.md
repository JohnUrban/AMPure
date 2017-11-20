# AMPure
Script for figuring out AMPure ratios needed for size selection, etc.


John Urban (2010-2017)

I created this AMPure tool circa 2010-2011. I'm sharing this for others at The Carnegie Institution, as well as anyone else, to use.

It is modeled using data from a series of experiments where I explored the effects of different AMPure ratios on DNA size that stays in the supernatant or goes on the beads.

The boundaries are not sharp cutoffs by any means - and where I decided to set the boundaries was subjective based on my experience with it.



    John Urban (2010-2017)
    Created 2010.
    Updated Nov 20, 2017: more helpful help message, recipe for any volume (not just 100 ul).


    Usage 1: Give floor and ceiling sizes.
        Find the first and second ratio to use for given floor and ceiling boundaries (e.g. 200 to 500).
    Syntax:
        AMPure minSize maxSize
    Example:
        AMPure 200 500



    Usage 2: Given floor and ceiling ratios.
        Find the floor and ceiling given a pair of ratios to use (e.g. 0.7 to 1.0).
    Syntax:
        AMPure minRatio maxRatio
    Example:
        AMPure 0.7 1.0



    Usage 3:
        Get the recipe in 100 ul as the output for Usage 1 or Usage 2.
    Syntax:
        AMPure minSize maxSize recipe
        AMPure minSize maxSize r
        AMPure minRatio maxRatio recipe
        AMPure minRatio maxRatio r
    Example:
        AMPure 200 500 r
        AMPure 0.7 1.0 r



    Usage 4:
        Get the recipe in YOURCHOICE ul as the output for Usage 1 or Usage 2.
        ((volume in ul))
    Syntax:
        AMPure minSize maxSize r volume
        AMPure minRatio maxRatio r volume
    Example:
        AMPure 200 500 r 200
        AMPure 0.7 1.0 r 200



    Usage 5:
        Show Size-vs-Ratio linear model x,y pairs starting at 200 bp up to 800 bp in given stepSize intervals.
    Syntax:
        AMPure stepSize
    Example:
        AMPure 50
        AMPure 100
        AMPure 200
        
    This will print a table of sizes 200-800 in stepSize intervals.
    'Size' is the boundary size:
        DNA > Size is on the beads
        DNA < Size is in the supernatant

        
    Overall, the linear model in this script works (approximately) for ratios in between 0.4-1.0, which outlines a size range of 200-800 bp.
    As the ratio gets smaller, the boundary is less precise.
    In fact, I used 0.4x to deplete DNA < 1-2 kb in MinION preps. Nonetheless, it definitely depletes DNA < 800 bp.


    I've used this program to outline floors/ceilings for a lot of Illumina preps targeting fragments in between
    200-800 bp, and it seems to work like a charm. In particular, for all steps that involve AMPure in Illumin preps,
    I always use the floor ratio to deplete DNA smaller than my ultimate target insert size.
    I do both floor and ceiling cutoffs both before AND after PCR.
    If really tight cutoffs are needed, you can repeat the floor/ceiling size-selection s.t. you do it twice before and twice after PCR.
    You need to adjust ratios at each step that adds length to the DNA fragments you are working with.
    For NEBNext preps, size is added after adapter ligation AND after PCR.
    



