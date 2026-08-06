{{ partial "header" . }}

{{ partial "title" . }} {{ with .Content }}{{.}}{{ end }}

{{ $latestcount := .Site.Params.LatestCount | default 3 }} {{ $postsection := .Site.Params.PostSection | default "post" }} {{ with .Site.GetPage "section" $postsection }}

#### {{ T "latestPost" }}

{{- range (first $latestcount (where .Pages "Section" $postsection)) -}} {{ partial "li" . }} {{- end -}}

{{ end }} {{ $worksection := .Site.Params.WorkSection | default "work" }} {{ with .Site.GetPage "section" $worksection }}

#### {{ T "latestWork" }}

{{- range (first $latestcount (where .Pages "Section" $worksection)) -}} {{ partial "li" . }} {{- end -}}

{{ end }}

{{ partial "footer" . }}