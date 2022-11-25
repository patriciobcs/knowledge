- #+BEGIN_QUOTE
  “I begin to speak only when I’m certain what I’ll say isn’t better left unsaid.” – Cato
  #+END_QUOTE
- query-table:: false
  #+BEGIN_QUERY
  {
  :title [:h2 "Topics"]
   :query [
           :find (pull ?p [*]) 
           :where 
           (has-page-property ?p :type)
           ]
  }
   :result-transform (fn [result]
                        (sort-by (fn [h]
                                   (get h :block/updated-at)) result))
  :breadcrumb-show? true
   :collapsed? true
  #+END_QUERY
-