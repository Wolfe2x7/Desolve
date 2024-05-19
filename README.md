![utah_teapot](https://github.com/Wolfe2x7/Desolve/assets/72348938/1151225f-dd9f-4b3e-aa6c-c26b97ea1902)
# Desolve ('dissolve')
Run a copy of this script inside your project to convert a 3D model in OBJ format to Defold's mesh vertex buffer format, useful for wireframe rendering. It can also convert to a regular triangulated mesh. When creating a wireframe, faces do not have to be triangulated; quads and Ngons will be traced as they are.

Change the variables in the script to input your OBJ file and desired output filename. The buffer file will include a dummy stream named "aabb", containing the extents of the OBJ model. Copy and paste those values to a script to enable frustum culling for your new mesh, like this example:
```
function init(self
	-- set AABB for mesh
	local res_path = go.get('#mesh', 'vertices')
	local buf = resource.get_buffer(res_path)
	buffer.set_metadata(buf, hash('AABB'), { -1, -1, -1, 1, 1, 1 }, buffer.VALUE_TYPE_FLOAT32)
	resource.set_buffer(res_path, buf)
end
```

Note: This may not work with older/unusual OBJ formats.
