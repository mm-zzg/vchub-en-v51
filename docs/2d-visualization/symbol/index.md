# Symbol

Symbols are a simple yet powerful feature that can be used alongside other windows. A Symbol is a component in graphical interface design that can contain various elements, such as images, controls, label, and more, which can be operated and managed as a single unit. Symbols are reusable and can be used in multiple places. If the symbol template is modified, all instances of that symbol are updated simultaneously. This makes symbols particularly useful for displaying similar interface elements or data and simplifies the maintenance and management of the interface.

Symbols also support nesting, which involves embedding one symbol within another, similar to using controls. This approach is particularly useful for breaking a project into multiple similar widgets. For example, you can create a universal pressure gauge symbol and then embed it into symbols for tanks, motors, and compressors. By setting up the pressure gauge symbol once, you can apply it in multiple places throughout the project, avoiding repetitive work.

## Symbol Properties

Symbol properties allow each symbol instance to reference different data, enabling flexible configuration. The primary purpose of symbols is to simplify and maintain repetitive user interface elements, making correct use of symbol properties crucial.

**Background**

This property is only visible in the symbol editor and is used for internal symbol settings. It will not be displayed in the symbol instances and cannot be bound to other controls, but it can be bound within the symbol editor.

**Custom Property**

Custom properties allow for personalized configuration of each symbol instance. For example, in the case of a motor symbol, you can set a `MotorNumber` parameter. This parameter can be used as a dynamic variable within the symbol instance, ensuring consistency and convenience in configuration. Properties defined in the symbol editor can be bound in the instance, but they cannot be bound within the editor itself.