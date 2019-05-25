Rage
====

By joaquimandrade and Arkshine

AMX Mod X Module.

It works as follow :

Let's say we want to use a function that we can't use no matter what with amxx by itself :
First, we need to create a component called handler in C++ that is like a module but its purpose its to handle the management
of the hooking and calling of the function by plugins and rage modules alike. Basically, it links plugins and rage modules
to the function. They are relatively easy to create since we can use one already made as skeleton to create other one.
There must be one per function header. For example:
int CBasePlayerWeapon::AddPrimaryAmmo( int iCount, char *szName, int iMaxClip, int iMaxCarry )
It returns an int, its a member function of class CBasePlayerWeapon, and its arguments types are int char* int int.
So, we would need an handler for it that would take this into account and then we can use the same handler for :
int CBasePlayerWeapon::AddSecondaryAmmo( int iCount, char *szName, int iMaxClip, int iMaxCarry )
Since it has the same header. The function in this case wouldn't need to be exactly a member of CBasePlayerWeapon since all entities are
supposed to be handled the same way.
This way is more painful than in orpheu but it was a must for rage because having no restrictions was a must.
We well give examples for some cases and help you if you need.
Now assuming we have an handler to the function we want to hook we would need to create a file like in orpheu for it.
I will talk about those files in a specific thread so, for now, check in examples to see how they look.

Now assuming we have an handler and a file for the function we can from now call it and hook it in amxx plugins and rage modules with
the natives that rage provides.
At the end, you have this flow :


Notes :
- We are releasing this as BETA because we want to have sure that its API is ok to start to create handlers without having to worry
because of future updates that rage might have to take so we would ask for people to try to start creating handlers and sub modules
to test the API and features it might need to get added.

- Rage doesn't have the restriction that made orpheu unable to get to the amxmodx tree so hopefully it can be integrated in amxmodx.
We are open to change it's code to make it fit for it if someone thinks is ok to.

- If you are more into making plugins and not much into C++ you better wait for people creating sub modules that provide functionality directly
to plugins instead of trying to use rage. 

- Rage won't come directly with natives for memory patching but it makes it easy to create a module like this http://forums.alliedmods.net/showthread.php?t=23152
as submodule and with support to signatures.
So this is it for now. Expect threads in Code Snippets/Tutorials from now on on teaching how to use this module for specific tasks step by step.

Update:

Beta 2 Changelog:
Added alias handling (now czero uses cstrike files)
Added some functions to FunctionForModule
Fixed some stuff

Beta 3 Changelog:
Fixed problem with long handler filename. (buffer related)
Fixed bug with a hook could not be removed.

Beta 4 Changelog:
Fixed some depreciation warnings
Added SSE2 and other optimisations
