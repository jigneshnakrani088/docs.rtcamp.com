---
title: rtp_head
---

### Description


Used to add style/scripts after wp_head hook before closing of head tag.


### Example



    
    function custom_rtp_head() { ?>
    <p>This code is call after wp_head hook and before closing of head tag. </p><?php
    }
    add_action( 'rtp_head', 'custom_rtp_head' );
