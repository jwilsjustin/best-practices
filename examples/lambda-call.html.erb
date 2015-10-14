# In the controller
@data = lambda { Post.where("created_at > ?", 10.days.ago) }

# In the view
<% @data.call.each do |post| %>
  <%= post.title %>
<% end %>

# This is especially nice if you cache the view
<% cache ["recent_posts"], expires_in: 30.minutes do %>
  <% @data.call.each do |post| %>
    <%= post.title %>
  <% end %>
<% end %>
