# Projects

## **What is a project?**

Projects are used to manage the visualization elements of the VC Hub system, and through multi-project management, it is possible to clearly differentiate between the presentation and design of configuration screens in several industrial application scenarios. In a project, **configuration controls**, **tag** **s** and **scripts** allow the user to freely configure a variety of digital visualization interfaces in order to cope with different industrial production scenarios.

In the VC Hub system, the project is a configuration unit that contains:

- [2D Configuration](../../2d-visualization/index.md): A rich graphical configuration editor.
- [3D Configuration](../../3d-visualization/index.md): A three-dimensional graphical configuration editor, which, once configured, can be displayed on the screen by means of the 3D controls in the **2D Configuration**.

In a single project, multiple configuration pages can be managed at the same time, the project can be seen as a folder of multiple related configuration screens. Through this mechanism, in an industrial generation environment with relatively more scenes, users can create multiple projects, each managing a production scene in the project, and a production scene consists of multiple screens to achieve the goal of clear management of configuration screens, and to make the later maintenance easier.

For example, there is a large factory with 10 production plants.

Under the project management mechanism, you can create a project called "Factory", which contains general information about the factory production and overview controls and data of the 10 workshops.

At the same time, you can create a project called "Factory", which contains general information about the production of the factory and an overview of the 10 workshops, as well as data for each of the 10 workshops.

Through the screen jump function in the configuration, the workshop controls in the overview screen of the "Factory" and the screens in each workshop project are associated to realize the multi-level management of the production environment.

## **How to use**

After successfully logging in to the system, users will be taken to the project list page, where they can manage their projects.

![alt text](1.png)


**There are two Auto Login status shown in the project list: Enabled, and Disabled.**

- **Enabled**: The auto login feature has been turned on in the project configuration window within the editor.
- **Disabled**: The auto-login feature for the project is disabled. If the project was added to the project list via import, a special icon will be displayed next to the "Disabled" status.

**Project Configuration Window**:

![alt text](2.png)

Projects are presented in both lists and charts, which are switched via the icon in the upper left corner.

The default mode is list view.

![alt text](3.png)


| Icon |  Description   |                                  
|-------------|--------------|
| ![alt text](4.png)| Use chart mode to display. <br> ![alt text](7.png)|
| ![alt text](6.png)| Use list mode to display. <br> ![alt text](5.png)|

#### **Query**

Users in the main page of the project, you can view all the projects in the current system. By default, projects are sorted in descending order by creation time. Users can also customize the sorting as needed. Currently, sorting by creation time or project name in both ascending and descending order is supported.

Users can switch the project to display in list or arrangement mode through the button on the upper left corner, the default is to display in list mode, after clicking the arrangement mode on the left side, as shown in the figure below, only the project name and project picture are displayed.

Users can input the keywords of the **project name** through the input box at the upper right corner to filter out the projects to be displayed by fuzzy filtering.

![alt text](8.png)


#### **Add**

![alt text](9.png)


Users can create a new project by clicking on the Add button in the upper right corner button and entering the basic information of the project.

| **Configuration**   | **Description**  |
|---------------------|----------------------|
| Project Name        | The name of the project, the name cannot be repeated, required.  |
| Project Description | The description of the project, optional.  |
| Project Image       | The image that will be displayed when the project is arranged, only JPG, GIF, PNG, SVG, JPEG format is supported. Optional. If no customized image is uploaded, the default image will be displayed, as shown in the query function. |

#### **Design**

Select any project and click Design button to open the project design page.

![alt text](10.png)


![alt text](11.png)


Please refer to: [2D Configuration](../../2d-visualization/index.md), [3D Configuration](../../3d-visualization/index.md), [Assets and Tags](../assets-and-tags/index.md) for specific function introduction of the design page.

#### **Run**

Select any project and click the **Run** button to open the project **startup page.**

![alt text](12.png)


The **startup page** can be set in the “Project Configuration” window of the 2D Designer.

![alt text](13.png)


#### **Copy**

Select any project, click **Copy** button , an edit box will pop up, the default name of the copied project is "{original project name}_Copy", users can modify the name, description and project picture according to requirements.

![alt text](14.png)


![alt text](15.png)


Click  the “OK “  button to complete the copy.

![alt text](16.png)



#### **Edit**

The user can move the mouse over any of the Project **More** buttons, which will display more drop-down menu options.

![alt text](17.png)


After the user clicks on the drop-down menu **Edit** button, the project base information edit box will pop up, modify it as needed and click **OK** to modify the project base information.

![alt text](18.png)


#### **Delete**

After the user clicks on the drop-down menu Delete button, a Delete prompt box will pop up, click on OK to delete the selected item. Message.

![alt text](19.png)


#### **Export**

 Users can move their mouse over any of the project "More" buttons to reveal more drop-down menu options.

![alt text](20.png)

 After the user clicks on **Export** , the selected items can be exported to a  wsproj  file, which can be used for project backup.

#### **Import**

Users can click the Import button in the upper right corner to import the previously exported file, which will be imported with the file name of the wsproj file as the name of the project, and the time of import will be added after the file name as the name of the imported project.

![alt text](21.png)


## **Asset Window in Project**

In the Project Designer, users can view and edit the asset model and asset instances in the asset list in the lower left corner, but the special thing is that the asset data doesn't belong to a single project, for example, if the user has added the tag n in Project A, the tag will be equally visible in Project B and you can use it.

**Note**: Asset data does not belong to the project, the asset exists independently in the system, and there is only a usage relationship between the project and the asset.

![alt text](22.png)







