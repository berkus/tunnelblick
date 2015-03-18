# System Folder Ownership and Permissions #



&lt;hr&gt;



### System Folder Security ###
One aspect of computer security is the security of system files and folders -- files and folders created by OS X to run your computer. The security is primarily controlled by the ownership and permissions of the files and folders that make up OS X and the applications and data on your computer.

Tunnelblick checks the security of itself and of the parts of OS X that it uses. That sometimes results in Tunnelblick complaining that a system folder is not secure, and refusing to connect a VPN. For example, you might see the following message after launching Tunnelblick:

<img src='https://www.tunnelblick.net/images/ApplicationsFolderNotSecure.png' width='50%'><br />

Other problems with system folder security may only appear when you try to connect to a VPN.<br>
<br>
Tunnelblick repairs the security of all of its own files and folders, but does not repair files and folders that it does not create, such as system folders.<br>
<br>
<h3>How System Folders Become Insecure</h3>
System folders are secure when OS X is installed, and usually only become insecure as the result of a program installer behaving improperly. System folders could become insecure because of malware, but that is rare:<br>
<ul><li>In May 2014, Apple's iTunes 11.2 update caused each system boot to set insecure permissions on /Users and /Users/Shared. This was corrected in iTunes 11.2.1.<br>
</li><li>There are reports that some MacPorts installers makes /usr insecure, and that some SPSS and xQuartz installers and some player application installers for Vulkano streaming video make /Applications insecure.</li></ul>

<h3>Repairing System Folder Security</h3>
On OS X 10.6 and higher, the ownership and permissions of system folders can be repaired by using the "Disk Utility" application (/Applications/Utilities/Disk Utility). Select the boot volume in the list on the left, and do a "Repair Disk Permissions".<br>
<br>
Disk Utility in OS X 10.5 and lower does not fix the ownership and permissions of system folders; they must be repaired manually using the Terminal application (/Applications/Utilities/Terminal).<br>
<br>
<h3>Correct System Folder Ownership and Permissions</h3>
System folder ownership and permissions vary from folder to folder and from one version of OS X to another. The following table lists the standard (secure) ownership and permissions for selected system folders under various versions of OS X.<br>
<br>
<b>For OS X 10.7 - 10.9:</b>
<table><thead><th> Folder                                   </th><th> Owner  </th><th> Group </th><th> Permissions </th><th> Octal </th><th> <font color='red'>Use "Repair Disk Permissions" in Disk Utility</font>  </th></thead><tbody>
<tr><td> /Applications                        </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td></tr>
<tr><td> /Library                                 </td><td> root     </td><td> admin </td><td> rwxrwxr-t    </td><td>1775 </td></tr>
<tr><td> /Library/Application Support </td><td> root     </td><td> wheel </td><td> rwxrwxr-t    </td><td> 1775 </td></tr>
<tr><td> /Users                                   </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td></tr>
<tr><td> /usr                                      </td><td> root     </td><td>  wheel </td><td> rwxr-xr-x    </td><td> 0755 </td></tr></tbody></table>

<b>For OS X 10.6:</b>
<table><thead><th> Folder                                   </th><th> Owner  </th><th> Group </th><th> Permissions </th><th> Octal </th><th> <font color='red'>Use "Repair Disk Permissions" in Disk Utility</font>  </th></thead><tbody>
<tr><td> /Applications                        </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td></tr>
<tr><td> /Library                                 </td><td> root     </td><td> wheel </td><td> rwxr-xr-x    </td><td> 0755 </td></tr>
<tr><td> /Library/Application Support </td><td> root     </td><td> admin </td><td> rwxr-xr-x    </td><td>0755 </td></tr>
<tr><td> /Users                                   </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td></tr>
<tr><td> /usr                                      </td><td> root     </td><td>  wheel </td><td> rwxr-xr-x    </td><td> 0755 </td></tr></tbody></table>

<b>For OS X 10.5:</b>
<table><thead><th> Folder                                   </th><th> Owner  </th><th> Group </th><th> Permissions </th><th> Octal </th><th> Terminal command to repair</th></thead><tbody>
<tr><td> /Applications                        </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td><td> sudo chown root:admin /Applications; sudo chmod 0775 /Applications </td></tr>
<tr><td> /Library                                 </td><td> root     </td><td> admin </td><td> rwxrwxr-t    </td><td>1775 </td><td> sudo chown root:admin /Library; sudo chmod 1775 /Library </td></tr>
<tr><td> /Library/Application Support </td><td> root     </td><td> wheel  </td><td> rwxr-xr-x    </td><td>0755 </td><td> sudo chown root:wheel /Library/Application Support; sudo chmod 0755 /Library/Application Support </td></tr>
<tr><td> /Users                                   </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td><td> sudo chown root:admin /Users; sudo chmod 0775 /Users </td></tr>
<tr><td> /usr                                      </td><td> root     </td><td>  wheel </td><td> rwxr-xr-x    </td><td> 0755 </td><td> sudo chown root:wheel /usr; sudo chmod 0755 /usr </td></tr></tbody></table>

<b>For OS X 10.4:</b>

<table><thead><th> Folder                                   </th><th> Owner  </th><th> Group </th><th> Permissions </th><th> Octal </th><th> Terminal command to repair </th></thead><tbody>
<tr><td> /Applications                        </td><td> root     </td><td> admin </td><td> rwxrwxr-x   </td><td> 0775 </td><td> sudo chown root:admin /Applications; sudo chmod 0775 /Applications </td></tr>
<tr><td> /Library                                 </td><td> root     </td><td> admin </td><td> rwxrwxr-t    </td><td>1775  </td><td> sudo chown root:admin /Library; sudo chmod 1775 /Library </td></tr>
<tr><td> /Library/Application Support </td><td> root     </td><td> admin  </td><td> rwxrwxr-x   </td><td>0775 </td><td> sudo chown root:admin /Library/Application Support; sudo chmod 0775 /Library/Application Support </td></tr>
<tr><td> /Users                                   </td><td> root     </td><td> admin </td><td> rwxrwxr-t    </td><td>1775  </td><td> sudo chown root:admin /Users; sudo chmod 1775 /Users </td></tr>
<tr><td> /usr                                      </td><td> root     </td><td>  wheel </td><td> rwxr-xr-x    </td><td> 0755  </td><td> sudo chown root:wheel /usr; sudo chmod 0755 /usr </td></tr></tbody></table>



<hr />
<h3>PLEASE USE THE <a href='https://groups.google.com/forum/#!forum/tunnelblick-discuss'>TUNNELBLICK DISCUSSION GROUP</a> FOR COMMENTS OR QUESTIONS