2025-09-02 15:29

Status:

Tags: [[MagicDraw]] 

There are a couple ways to do this. 

We are trying to trace FMEA items back to our PL Spec. I am going to determine which requirements I think fit and then we will have a meeting with Kateri. 

1. Right click on requirement
2. Go to Specification window (this is where all of the info for elements inside the model is stored, set properties to All)
3. There is a Traceability tab at the bottom of the Specification window.
4. Click into Relations in the left column. 
5. Click Create Outgoing. 
6. Click Trace. This will prompt you to search for an element to trace to. Make sure you're filtered for any element.
7. Navigate to FMEA IDs and click the one you want to tie a trace to. 

The reason that we're doing this is so that in our FMEA Map, we have a visual of how each FMEA item/failure mode connects to previously defined requirements. 

Once requirements are traced to FMEA items, relation map is populated by clicking three dots next to Relation Criteria on FMEA Map. It will show all of the different types of relation criterion, make sure Item Relation is true so that the FMEA ID connections to the proxy ports are visible. 

Going to have to play around to find out what gets the connections to show. 
# References
