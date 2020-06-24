# tips

### This is a random file/repo I'll write down some useful stuff for future reference.

----

*Blender's ESCN exporter for Godot:*

Ok.....

here's how the material nightmare works. (for the blender ESCN exporter)

the "material search path" is not the scene's dynamic lookup for the material file. it's done on EXPORT when the blender exporter parses through the project folders to see if there's a matching material that's already been prepped in godot - if there is, the exporter will set the escn file to look for that path instead!

the "generate external material" doesn't toggle between internal and external materials either!!! the blender exporter doesn't actually save any material files, that's the importer saving them into file! if unchecked, blender will NOT export materials. to have materials in godot, you NEED external material files. Godot's importer WILL save materials as separate files, if there are materials... which brings to the "mesh" vs "node" material check on godot's importer: that only toggles between assigning the material to the *mesh* node and the *spatial* node... because in some specific cases the former doesn't quite work for some reason
since the importer has a "keep on import" which means the importer will NOT re-save the material - it will keep the previous file. also the ESCN's exporter lookup only works with [name].tres

oh, and the ESCN exporter doesn't quite work with spatial materials. they appear invisible (albedo set to full transparency) whereas the normal dae export (import) saves spacial .material files just fine!

also, this is all made worse by the fact that Godot's imports are... kinda flaky. they work, but the display is cached, and the mess gets worse with ESCN scene files.... on reimport/refresh the mesh explodes sometimes, and material changes sometimes aren't shown until you refresh the scene/close down the parent/open and close the imported file
