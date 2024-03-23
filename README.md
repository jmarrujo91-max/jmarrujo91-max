hello-world ### Hi there 👋
CREATE[JM1] TABLE [follows] (
  [following_user_id] integer,
  [followed_user_id] integer,
  [created_at] timestamp
)
GO

CREATE TABLE [users] (
  [id] integer PRIMARY KEY,
  [username] nvarchar(255),
  [role] nvarchar(255),
  [created_at] timestamp
)
GO

CREATE TABLE [posts] (
  [id] integer PRIMARY KEY,
  [title] nvarchar(255),
  [body] text,
  [user_id] integer,
  [status] nvarchar(255),
  [created_at] timestamp
)
GO

EXEC sp_addextendedproperty
@name = N'Column_Description',
@value = 'Content of the post',
@level0type = N'Schema', @level0name = 'dbo',
@level1type = N'Table',  @level1name = 'posts',
@level2type = N'Column', @level2name = 'body';
GO

ALTER TABLE [posts] ADD FOREIGN KEY ([user_id]) REFERENCES [users] ([id])
GO

ALTER TABLE [follows] ADD FOREIGN KEY ([following_user_id]) REFERENCES [users] ([id])
GO

ALTER TABLE [follows] ADD FOREIGN KEY ([followed_user_id]) REFERENCES [users] ([id])
GO


<!--
**jmarrujo91-max/jmarrujo91-max** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
