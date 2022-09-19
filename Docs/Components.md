# Which files implement which components?

This list shows which code files are responsible for which parts of Policy Plus's functionality. Only `.vb` files are included; the corresponding `.Designer.vb` and `.resx` files are machine-generated.

* `AdmlFile.vb`: Defines the `AdmlFile` class, which represents an administrative template's language resource file (the one that contains the language-specific texts). That information is loaded from ADML files parsed as XML. By themselves, these objects are not terribly interesting; they go along with a corresponding `AdmxFile` instance.
* `AdmxBundle.vb`: Defines the `AdmxBundle` class, which represents a policy workspace. Information is taken out of multiple `AdmxFile` and `AdmlFile` instances and processed to discover properties of and relationships between policy objects. Bundle objects serve as links between ADMX data and ADML data, providing methods to resolve text from a language-neutral identifier. Also defines the `AdmxLoadFailType` enumeration and `AdmxLoadFailure` class, which represent problems encountered while trying to add ADMX files to the bundle.
* `AdmxFile.vb`: Defines the `AdmxFile` class, which represents an administrative template's policy objects: categories, policies, products, and support definitions. That information is loaded from ADMX files parsed as XML. All text in these files is language-neutral; the ADML files provide the human-readable strings.
* `AdmxStructures.vb`: Defines several classes used to hold information extracted from ADMX files. Since ADMX files rarely make sense on their own, these classes have minimal interconnectedness. Rather, string fields hold the IDs of referenced policy objects.
* `BitReinterpretation.vb`: Defines explicit-layout structures used to reinterpret signed integers/longs as unsigned or vice versa so that large unsigned values can be read or written from the Registry using the standard `RegistryKey` class. 
* `CmtxFile.vb`: Defines the `CmtxFile` class, which represents a comments file, which holds the user's annotations on policy settings. Information can be loaded from and saved to a CMTX file (XML format). For ease of use, the class also provides methods for translating policy-ID-to-comment mappings to `CmtxFile` instances and back.
* `CompiledStructures.vb`: Defines several interconnected classes used to hold information about policy objects. `AdmxBundle` creates these by weaving together information from several ADMX and ADML files. These instances are the object-oriented equivalents of their `AdmxStructures.vb` counterparts.
* `ConfigurationStorage.vb`: Helps load and store program configuration that resides in the Registry.
* `DetailAdmx.vb`: Defines the form that presents internal information on an ADMX file object (`AdmxFile`) and lists the objects it defines.
* `DetailCategory.vb`: Defines the form that presents internal information on a category object (`PolicyPlusCategory`).
* `DetailPolicy.vb`: Defines the form that presents internal information on a policy object (`PolicyPlusPolicy`).
* `DetailProduct.vb`: Defines the form that presents internal information on a product object (`PolicyPlusProduct`).
* `DetailSupport.vb`: Defines the form that presents internal information on a support definition object (`PolicyPlusSupport`).
* `DownloadAdmx.vb`: Defines the form that allows the user to download the full set of administrative templates from Microsoft. The user may set a download location or install the templates in the default folder. Once the download is complete, the form can open the new workspace.
* `EditPol.vb`: Defines the *Edit Raw POL* window, which allows the user to directly modify the Registry-based policy data in a POL-backed policy source.
* `EditPolDelete.vb`: Defines the *Delete Value(s)* form, which allows the user to specify which values under a key to delete. This form is always shown as a child of *Edit Raw POL*.
* `EditPolKey.vb`: Defines the *New Key* form, which allows the user to add a new key from the *Edit Raw POL* dialog.
* `EditPolMultiStringData.vb`: Defines the *Edit String List* form, which allows the user to edit the data of a multi-string value from *Edit Raw POL*.
* `EditPolNumericData.vb`: Defines the *Edit Number* form, which allows the user to edit the data of a DWord or QWord value from *Edit Raw POL*. This file also defines the `WideRangeNumericUpDown` control class, which works like a normal `NumericUpDown` but does not misbehave when editing large numbers in hexadecimal mode.
* `EditPolStringData.vb`: Defines the *Edit String* form, which allows the user to edit the data of a string or expandable string value from *Edit Raw POL*.
* `EditPolValue.vb`: Defines the *New Value* form, which allows the user to add a new value and specify its type from *Edit Raw POL*.
* `EditSetting.vb`: Defines the *Edit Policy Setting* form, which allows the user to reconfigure the state of a specific policy. This class is responsible for creating the UI elements (e.g. text boxes, check boxes) corresponding to the policy elements. It also provides a text box for comment editing. When the user saves the policy state, the form converts the user's input in the UI elements to the appropriate .NET Framework type.
* `ExportReg.vb`: Defines the *Export REG* window, which allows the user to export a policy source or a branch thereof to a REG file using a specified prefix.
* `FilterOptions.vb`: Defines the *Filter Options* window, which allows the user to narrow down the policy settings shown in the main window. The user may filter by type (policy vs. preference), current state, whether the setting is commented, and which systems support the policy.
* `FindById.vb`: Defines the *Find by ID* window, which allows the user to jump to a policy object by its unique ID.
* `FindByRegistry.vb`: Defines the *Find by Registry* window, which allows the user to search for policies by Registry keys or values affected. Wildcards are supported.
* `FindByText.vb`: Defines the *Find by Text* window, which allows the user to search for policies by text in their titles, descriptions, or comments. Wildcards and multi-word literals are supported.
* `FindResults.vb`: Defines the *Search Results* window, which performs and reports on searches done by the *Find by Registry* and *Find by Text* windows. Searches are defined by functions that take a policy and return whether the policy is a match.
* `ImportReg.vb`: Defines the *Import REG* window, which allows the user to import a REG file into a policy source. The user can specify the REG file's prefix, but the form uses `RegFile`'s guessing ability to suggest a likely prefix when a file is selected.
* `ImportSpol.vb`: Defines the *Import Semantic Policy* window, which allows the user to type, paste, or load a Semantic Policy script. The user may then apply it to the current policy sources or only validate it.
* `InspectPolicyElements.vb`: Defines the *Element Inspector* window, which displays the details of how the selected policy applies to the Registry.
* `InspectSpolFragment.vb`: Defines the *Semantic Policy Fragment* window, which displays Semantic Policy text that represents the current state of the selected policy.
* `LanguageOptions.vb`: Defines the *Language Options* window, which allows the user to change the preferred ADML language. This form is launched by the *File | Set ADML Language* menu item.
* `ListEditor.vb`: Defines the *Edit List* window, which allows the user to configure a list policy element. This form is launched by the setting editor.
* `LoadedAdmx.vb`: Defines the *Loaded ADMX Files* window, which displays the filename, path, and namespace of all loaded ADMX files. Double-clicking an entry opens the selected ADMX file in *ADMX Details*.
* `LoadedProducts.vb`: Defines the *All Products* window, which allows the user to explore the hierarchy of defined products. Double-clicking an entry opens the *Product Details* window.
* `LoadedSupportDefinitions.vb`: Defines the *All Support Definitions* window, which displays all defined support definitions and allows the user to filter them by name. Double-clicking an entry opens the *Support Details* window.
* `Main.vb`: Defines the application's main window. This file launches all other forms and in most cases carries out the actions taken by the user in those forms.
* `OpenAdmxFolder.vb`: Defines the *Open ADMX Folder* window, which allows the user to load a set of policy definitions (ADMX and ADML files) from the default local location, the domain's SYSVOL, or a custom location (if the computer is domain-joined).
* `OpenPol.vb`: Defines the *Open Policy Resources* dialog, which allows the user to select a policy source for the two sections. Both sections support the local GPO, a local Registry branch, a POL file, and nothingness (a scratch space). The user section also supports a per-user GPO and a user Registry hive.
* `OpenSection.vb`: Defines the *Select Section* window, which allows the user to choose the section to which an operation (e.g. a POL import) applies.
* `OpenUserGpo.vb`: Defines the *Select User SID* window, which allows the user to enter a SID or search for a SID by username when opening a user GPO from the *Open Policy Resources* dialog.
* `OpenUserRegistry.vb`: Defines the *Open User Hive* window, which displays the user profiles on the computer and whether their `ntuser.dat` hives are accessible. The user may choose one to select it into the *Open Policy Resources* dialog.
* `PInvoke.vb`: Defines the `PInvoke` class, which holds the definitions of native functions. This file also holds the .NET definitions of native structures used by those functions.
* `PolicyLoader.vb`: Defines the `PolicyLoader` class. Instances of this class are responsible for opening a policy source from a policy loader created by `OpenPol.vb`. Policy loaders are also responsible for saving changes, closing the policy sources, updating `gpt.ini`, providing the CMTX (comment) file path, and producing human-readable explanations of the policy source's status.
* `PolicyProcessing.vb`: Defines the `PolicyProcessing` class, which is responsible for all translation between policy state and Registry information in policy sources. This file also defines the `PolicyState` enumeration, which defines the basic policy states (e.g. Enabled), and the `RegistryKeyValuePair` class, which represents a Registry location.
* `PolicySource.vb`: Defines the `IPolicySource` interface and its two implementations. An `IPolicySource` object is responsible for saving and loading raw Registry data at the signal of `PolicyProcessing`. `PolFile` saves and loads that data POL files; `RegistryPolicyProxy` passes the commands directly through to the real Registry. The list of Registry branches that are considered policy sections is kept in `RegistryPolicyProxy`.
* `PolicyStructures.vb`: Defines several classes that represent policy elements and how they affect the Registry. This information is loaded only from ADMX files by `AdmxFile` and is used by `PolicyProcessing` to implement policy changes.
* `PresentationStructures.vb`: Defines several classes that represent policy presentations and their elements. This information is loaded only from ADML files by `AdmlFile`.
* `Privilege.vb`: Defines the `Privilege` class, which provides a convenience method `EnablePrivilege` that uses the P/Invoke methods in `PInvoke` to enable a privilege given its name.
* `RegFile.vb`: Defines the `RegFile` class, which loads and saves REG files for purposes of import to and export from policy sources. It implements just enough of `IPolicySource` to allow `PolFile.Apply` to work on it, but it cannot be used as an actual policy source.
* `SpolFile.vb`: Defines the `SpolFile` class, which parses a Semantic Policy script into a collection of policy states. These policy states are stored in `SpolPolicyState` instances, the class of which is also defined in this file. Each policy in a SPOL file has a section, a unique ID, a basic state, and optionally element states (if the policy is enabled).
* `SystemInfo.vb`: Defines functions that determine policy-related capabilities of the operating system.
* `Version.vb`: Autogenerated by `version.bat` to provide the last Git tag/commit in the `Version` constant.
* `XmlExtensions.vb`: Defines extension methods on `XmlNode` for convenience when loading XML files in `AdmxFile` and `AdmlFile`.