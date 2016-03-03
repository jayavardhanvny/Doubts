# Doubt

The headers can appear in any order, and servlets buffer the headers and send them all at once, so it is legal to set the
status code (part of the first line returned) even after setting headers. But servlets do not necessarily buffer the document 
itself, since users might want to see partial results
for long pages. Servlet engines are permitted to partially buffer the output, but the size of the buffer is left unspecified. 
You can use the getBufferSize method of
HttpServletResponse to determine the size, or you can use setBufferSize to specify it. You can set headers until the buffer 
fills up and is actually sent to the client.
If you aren’t sure whether the buffer has been sent, you can use the isCommitted method to check. Even so, the best approach 
is to simply put the setContentType
line before any of the lines that use the PrintWriter .
