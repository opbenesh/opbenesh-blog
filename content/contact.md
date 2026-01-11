---
title: "Contact"
layout: "contact"
summary: "Get in touch"
---

You can reach me via email at:

<span id="email-placeholder">Loading...</span>

<script>
    document.addEventListener('DOMContentLoaded', function() {
        // Simple obfuscation to prevent basic scrapers
        var user = 'opbenesh';
        var domain = 'gmail.com';
        var element = document.getElementById('email-placeholder');
        
        var a = document.createElement('a');
        a.href = 'mailto:' + user + '@' + domain;
        a.innerText = user + '@' + domain;
        
        element.innerHTML = '';
        element.appendChild(a);
    });
</script>
