step 1: payload selection

WHY THIS PAYLOAD)

Now :

Which characters break this context?

HTML body context:

Need to escape HTML

< > execution possible

Test payloads incrementally:

<
>
"
'

If < not escaped → good sign

Final payload choice:

<script>alert(1)</script>

WHY this payload?

<script> valid in HTML body

No user interaction needed

Simple execution proof
