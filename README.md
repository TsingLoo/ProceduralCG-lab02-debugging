# lab02-debugging

# Xiaonan Pan's Submission

Henry Han assisted me with the puzzles.
[Shadertoy Solution](https://www.shadertoy.com/view/tcsfWf)

## Bug List

1. The variable name `uv2`

   - The error info from shadertoy directly guides to its location
2. The width - height ratio, change `H` to `H *= len * iResolution.x / iResolution.y`; 
   - After the fix of bug 1., I notice the screen is kind of stretched, from my experience, this may relate  to the camera set and  screen resolution. As this project is raycast based, raycast is somehow the camera, so I go through its code first and find the problem
3. Replace `reflect(eye, nor)` by `reflect(dir, nor)`
   - Incorrect shading could come from incorrect hit info(like hitObjectID, shading model. material parameters) given by Intersection. I went to the Intersection and saw that the shading model is quite simple, just returning the color where the ray reflected to.  So, the missing reflection effects could be from the `reflect()` function as it goes to incorrect position to get color.
4. Increase the max iteration number of `march()`, and use `nor` instead of `dir` to offset the intersection to avoid the false negative hit near the object 
   -  The overall shapes looks smooth with a solid heigh-width ratio, so, the major of the code should be correct.
   - I just played with the parameters to see if any artifacts disappear.


# Setup 

Create a [Shadertoy account](https://www.shadertoy.com/). Either fork this shadertoy, or create a new shadertoy and copy the code from the [Debugging Puzzle](https://www.shadertoy.com/view/flGfRc).

Let's practice debugging! We have a broken shader. It should produce output that looks like this:
[Unbelievably beautiful shader](https://user-images.githubusercontent.com/1758825/200729570-8e10a37a-345d-4aff-8eff-6baf54a32a40.webm)

It don't do that. Correct THREE of the FIVE bugs that are messing up the output. You are STRONGLY ENCOURAGED to work with a partner and pair program to force you to talk about your debugging thought process out loud.

Extra credit if you can find all FIVE bugs.

# Submission
- Create a pull request to this repository
- In the README, include the names of both your team members
- In the README, create a link to your shader toy solution with the bugs corrected
- In the README, describe each bug you found and include a sentence about HOW you found it.
- Make sure all three of your shadertoys are set to UNLISTED or PUBLIC (so we can see them!)
