<h1>NoteCSharpDotNet</h1> 

<h2>View Data</h2>

<div>#Controller</div>
public IActionResult Create()
{
    IEnumerable<SelectListItem> list = _db.Villas.ToList().Select(x=> new SelectListItem
    {
        Text = x.Name,
        Value = x.Id.ToString()
    });
    ViewData["VillaList"] = list;
    return View();
}

<div>#View</div>
<div class="form-floating py-1 col-12">
   <select asp-for="@Model.VillaId" asp-items="@ViewData["VillaList"] as IEnumerable<SelectListItem>"
       class="form-select border shadow">
       <option disabled selected>--Select Viila--</option>
   </select>
    <label asp-for="VillaId" class="ms-2"></label>
    <span asp-validation-for="VillaId" class="text-danger"></span>
</div>
